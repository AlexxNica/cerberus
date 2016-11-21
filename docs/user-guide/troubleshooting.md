---
layout: documentation
title: Troubleshooting
---

# Excessive Polling

IPs making an excessive number of requests are automatically blacklisted for a configurable interval.

When using polling be sure to use a reasonable interval as determined by your organization.


# Permission Denied

#### E.g. com.nike.cpe.vault.client.VaultServerException: Response Code: 400, Messages: permission denied

The SDB you are trying to access may need permissions updated.  For example, you will get this error if the IAM
role being used isn't listed for the SDB you are trying to access.

Unexpectedly, you might also see this error when the path you are trying to access doesn't exist.

Please see [Vault Documentation](https://www.vaultproject.io/docs/http/) for more information on Vault errors.


# SSL Handshake Failure

#### E.g. javax.net.ssl.SSLHandshakeException: Received fatal alert: handshake_failure

We've seen this during local development as result of a library conflict with the
[jettyEclipseRun](https://github.com/Khoulaiz/gradle-jetty-eclipse-plugin) Gradle plugin.  Upgrading to the
[Gretty](https://github.com/akhikhl/gretty) plugin resolved.


# SSL Plaintext Connection Error

#### E.g. javax.net.ssl.SSLException: Unrecognized SSL message, plaintext connection?

During local development this may be due to a web proxy.  This is common in corporate environments and when working over a VPN.

If you are using the AnyConnect web proxy, it can be temporarily disabled with:

{% highlight bash %}

sudo /opt/cisco/anyconnect/bin/acwebsecagent -disablesvc -websecurity

{% endhighlight %}


# Outdated AWS SDK

#### E.g. com.amazonaws.util.EC2MetadataUtils methodname=getIAMSecurityCredentials Unable to process the credential, com.amazonaws.util.json.JSONException: Failed to instantiate class

You are probably using an older version of the AWS SDK.

### Gradle

Gradle users can see how dependencies are being resolved with the `gradle dependencies` command.

You can force a newer version by adding the following into your build.gradle

{% highlight groovy %}
// Use the newest version you can, this was current when we wrote this
final String AWS_SDK_VERSION = '1.10.5'
//noinspection GroovyAssignabilityCheck
configurations.all {
    resolutionStrategy {
        // add a dependency resolve rule
        eachDependency { DependencyResolveDetails details ->
            //Force use of certain dependencies or versions
            if (details.requested.group == 'com.amazonaws') {
                details.useVersion(AWS_SDK_VERSION)
            }
        }
    }
}
{% endhighlight %}

### Maven

Maven users can use the [dependency tree](http://maven.apache.org/plugins/maven-dependency-plugin/tree-mojo.html)
plugin to learn more about how dependencies are being resolved.
