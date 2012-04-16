---
layout: post
title: EF Code First & AppHarbor
---

Since my employer, [Improving Enterprises](href="http:/http://www.improvingenterprises.com/") lined me up a new gig that uses Entity Framework Code First, I thought I kick off a learning side project with MVC3 and deploy it to [AppHarbor](href="https://appharbor.com/". Everything seemed simple enough. Use Nuget to install the code first bits, hammer out a couple of model and a datacontext and BOOM! data goes into a database.

It wasn&#8217;t anything pretty, but I was ready to deploy it to AppHarbor. That sounded great, but my first deploy failed. The local build compiled and worked as expected. The source that I pushed to AppHarbor compiled without problem, but the deployment failed.

Problem number one, I didn&#8217;t create a database on AppHarbor. The quick solution was to configure the database on AppHarbor following their instructions. My local compile was fine and I expected my deployment to work as well. Wrong.

After a bit of googling, I found a reference to this [EF Tables only](href="http://nuget.org/List/Packages/EFCodeFirst.CreateTablesOnly"] Nuget package. From the package writeup:

<blockquote>Adds a IDatabaseInitializer implementation for EF Code First CTP5, as a workaround for situations where you need to update the tables, but can&#8217;t recreate the database. Works with AppHabor. To use simply set the DontDropDbJustCreateTablesIfModelChanged class as IDatabaseInitializer with DbDatabase.SetInitializer.</blockquote>

This package put a code file into the application&#8217;s App_Start folder. By un-commenting this line:

``` csharp "db initializer"
Database.SetInitializer( new DontDropDbJustCreateTablesIfModelChanged<MyContext>());
```

So, after following some clear instructions to configure my connection string with the AppHarbor standards and using this NuGet package, I now have my first MVC3 application successfully deployed to AppHarbor! Hopefully this will help others, but I&#8217;m happy just to have this information in a place where I&#8217;ll be able to find it again.

Now to tweak, prune and watch it grow into something that is emblematic of my learning.

Is this thing live, or memorex?
