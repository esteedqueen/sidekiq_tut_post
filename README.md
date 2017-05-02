Background jobs in rails applications make our development lives easier. 

We rely on them for a lot of things - common use cases include sending emails, push notifications, processing 3rd party API interactions, transactions and long-running requests that tie up server resources.

In a typical production app, there's a possibility of processing hundreds of jobs per second under normal circumstances and thousands depending on the number of users and campaign going on.

I've been using [Resque](https://github.com/resque/resque) for a while but recently made a switch to [Sidekiq](https://github.com/mperham/sidekiq). I initially wanted to write about the switch but I soon realized that the knowledge of introducing Sidekiq to a new project is important and the post became really long so I decided to split it. In this post, I'm going to show you how to use Sidekiq for your background jobs on a new rails app. And in part 2, I'll write about switching from an existing app with Resque to Sidekiq.

# Why Sidekiq?
I made the move for two reasons:
Failed jobs on Resque: 
![alt text][failedjobs]

[failedjobs]: https://github.com/esteedqueen/sidekiq_tut_post/images/resquefailedjobs.png "Failed jobs on Resque"

Apart from dealing with lots of failed jobs?
