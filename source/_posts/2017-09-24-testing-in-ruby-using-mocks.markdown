---
layout: post
title: "Testing in Ruby using mocks"
date: 2017-09-24 23:53:07 +0530
comments: true
categories:
---

Testing is a very important part of software development, and it doesn't just ends at you writing tests for your perfectly working code but writing tests before you write your perfectly working code i.e. follow TDD - Test Driven Development. And while you are doing all this you might have faced the problem where running your tests suite is taking a lot of time and hence increasing your development time. That's one reason why you would opt for mocking in your tests.

When unit testing, many times we find that the unit being tested depends on other units for it's functioning. These units can sometimes be difficult to work with because they might be dealing with a database, file IO or maybe a HTTP API. All of these can be slow at times, especially a HTTP API and increasing testing time as well as you might not want to hit an external HTTP API each time you run tests. Here comes in the use of [test-doubles](https://martinfowler.com/bliki/TestDouble.html). In Ruby [rpec-mocks](https://github.com/rspec/rspec-mocks) is one way to create these. Lets say you are working on a twitter app that has a PostController -


```
class PostController
  def create(user, title, article)
    post = Post.new(user, title, article)
    if post.save
      return true
    else
      return false
    end
  end
end
```
Here the unit being tested is create method and hence we do not care about the implementation of the dependencies like Post.

Now lets write the test for `PostController.create()` -
```
describe PostController do
  context "#create" do
    it "creates a new post for a given user"
      user = double("user")
      title = "Title"
      article = "Article"
      post = instance_double("post")
      expect(post).to receive(:save) { true }
      expect(Post).to receive(:new) { post }
      post_controller = PostController.new()
      expect(post_controller.create(user, title, article)).to eq(true)
    end
  end
end
```

In the above example you can see we have tried to verify if the unit being tested makes calls that it is supposed to and returns the expected value. By setting expectation on `:save` we ensure that if it is not called then the test will fail.

Here there is no need to worry about the `user` being queried for its details that are to be used in creation of a post, or how the `post` is actually going to save the details into the database and at the same time we are able to confirm that the functions required by the method `create` are being used by it.

Rspec-mocks provides a lot more similar functionalities that can be used to test more complex functions easily. For more details have a look at the rspec-mocks [documentation](https://github.com/rspec/rspec-mocks).

Mocking is a very opinionated topic just like testing itself. Some people believe that ideally all tests should be properly mocked while some believe otherwise. I have found mocking helpful because of the reasons I have mentioned above. The downside of mocking that I have felt is that sometimes you need to know some of the implementation details beforehand. I think there is no problem if you use mocking or not, the main thing to
note is that you test.
