Slack
=====

C# class for Slack Integration using API or Webhooks

#### Supports
		Slack API
		Slack Webhooks
============================
#### API Usage Exemple

##Simple Example

```
SlackClientAPI client = new SlackClientAPI();
string token = "xxxxx-xxxxx-xxxxx-xxxx";

Arguments p = new Arguments();
p.Channel = "#general";
p.Username = "fancy name";
p.Text = "Awesome Message";
p.Token = token;

client.PostMessage(p);
```

##Using Attachments and Response validation

```
SlackClientAPI client = new SlackClientAPI();
string token = "xxxxx-xxxxx-xxxxx-xxxx";

Arguments p = new Arguments();
p.Channel = "#general";
p.Username = "fancy name";
p.Text = "Awesome Message";
p.Token = token;

Attachment a = new Attachment();
a.Fallback = "some text";
a.Pretext = "some other text;
a.Color = "warning";

AttachmentFields af = new AttachmentFields();
af.Title = "Field 1";
af.Value = "Value 1";
af.Short = false;
a.Fields.Add(af);

AttachmentFields af2 = new AttachmentFields();
af.Title = "Field 2";
af.Value = "Value 2";
af2.Short = true;
a.Fields.Add(af2);

p.Attachments.Add(a);

client.PostMessage(p);

Response r = client.PostMessage(p);

if (!r.Ok)
{
    //oh noes something went wrong
}

```

#### API Usage Exemple
```
string urlWithAccessToken = "https://hooks.slack.com/services/xxxxxxx";
SlackClientWebhooks client = new SlackClientWebhooks();
//pretty much the same as above
```

Further info: https://api.slack.com/
