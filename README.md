# Greeting Card HTML Email Generator #

This project might interest you if

1. You hope and hypothesize that more and more **people are okay** with receiving a greeting card through email.
2. You want to add a degree of **personalization and style** to your emails without going through some other (branded) service.
3. You want to **style an email** beyond what your email client or service allows by default.
4. You are okay with **tinkering** with a tiny bit of Sass CSS, and running some commands in the terminal/command line.

This project is based on [Foundation for Emails](http://foundation.zurb.com/emails), a framework for creating responsive HTML devices that work in any email client. It has a Gulp-powered build system with these features:

- Handlebars HTML templates with [Panini](http://github.com/zurb/panini)
- Simplified HTML email syntax with [Inky](http://github.com/zurb/inky)
- Sass compilation
- Image compression
- Built-in BrowserSync server
- Full email inlining process

The following are features I added

- Write in markdown, compile to HTML
- Supports Chinese and English emails

## Workflow ##

1. Write your email as markdown. Put it in `src/pages`. Run `npm start` to keep an eye on how the email will look.
2. When you are ready for publishing, run `npm run build`.
3. Paste the resulting HTML page from the browser to your email.
4. Express gratitude and thanks to the people in your life!

## Limitations ##

- Images will likely still have to be brought in manually, or linked from somewhere on the web. Getting them into the content of your email programmatically sucks.
- Webfonts in emails are, at the time of writing, not very well supported beyond Apple products. \[[source](https://www.campaignmonitor.com/blog/email-marketing/2012/12/using-web-fonts-in-email/)\]

## Todo ##

- Programmatically upload images to s3 and change the img references from local to s3-hosted

## Installation

To use this template, your computer needs [Node.js](https://nodejs.org/en/) 0.12 or greater. The template can be installed with the Foundation CLI, or downloaded and set up manually.

Run this:

```bash
npm install
```

## Build Commands

Run `npm start` to kick off the build process. A new browser tab will open with a server pointing to your project files.

Run `npm run build` to inline your CSS into your HTML along with the rest of the build process.

Run `npm run litmus` to build as above, then submit to litmus for testing. *AWS S3 Account details required (config.json)*

Run `npm run zip` to build as above, then zip HTML and images for easy deployment to email marketing services.

## Litmus Tests (config.json)

Testing in Litmus requires the images to be hosted publicly. The provided gulp task handles this by automating hosting to an AWS S3 account. Provide your Litmus and AWS S3 account details in the `example.config.json` and then rename to `config.json`. Litmus config, and `aws.url` are required, however if you follow the [aws-sdk suggestions](http://docs.aws.amazon.com/AWSJavaScriptSDK/guide/node-configuring.html) you don't need to supply the AWS credentials into this JSON.

```json
{
  "aws": {
    "region": "us-east-1",
    "accessKeyId": "YOUR_ACCOUNT_KEY",
    "secretAccessKey": "YOUR_ACCOUNT_SECRET",
    "params": {
        "Bucket": "elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
    },
    "url": "https://s3.amazonaws.com/elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
  },
  "litmus": {
    "username": "YOUR_LITMUS@EMAIL.com",
    "password": "YOUR_ACCOUNT_PASSWORD",
    "url": "https://YOUR_ACCOUNT.litmus.com",
    "applications": ["ol2003","ol2007","ol2010","ol2011","ol2013","chromegmailnew","chromeyahoo","appmail9","iphone5s","ipad","android4","androidgmailapp"]
  }
}
```

For a full list of Litmus' supported test clients(applications) see their [client list](https://litmus.com/emails/clients.xml).

**Caution:** AWS Service Fees will result, however, are usually very low do to minimal traffic. Use at your own discretion.


