# BunnyWay.Metrics
BunnyWay.Metrics is a high performance .NET metrics tracker library that automatically sends data directly into InfluxDB 0.9.x.


### Configuration
It requires minimum configuration and is super easy to get started. The simplest way is to simply add the following settings into your app config file:
```xml
<appSettings>
    <add key="BunnyMetrics.InfluxDB.ServerUrl" value="http://127.0.0.1/" />
    <add key="BunnyMetrics.InfluxDB.DatabaseName" value="xxx" />
    <add key="BunnyMetrics.InfluxDB.Username" value="xxx" />
    <add key="BunnyMetrics.InfluxDB.Password" value="xxx" />
</appSettings>
```

### How to use
Tracking metrics and counters is easy
```C#
// Track a counter metric
MetricsTracker.Default.TrackMetric("WebApp.Login.FailedLoginAttempt");
```

```C#
// Track a metric
MetricsTracker.Default.TrackMetric("WebApp.ImageProcessing.QueueLength", 230);
```

```C#
// Track with tags
MetricsTracker.Default.TrackMetric("WebApp.ImageProcessing.QueueLength", 230, new Tag("ServerName", "as1"), new Tag("ServerGroup", "2"));
```

```C#
// Simple way to track timing
using (var timer = MetricsTracker.Default.TrackTimeMetric("WebApp.PasswordGeneration.Time"))
{
    Thread.Sleep(1000);
}```
