# vcr2

A package to mock requests using Dio Client, supports nullsafety.
Forked from the original vcr & maintained, it's a drop-in replacement.

## Getting Started

To start using, just create a adapter and put inside your client<br>
This is a example with Dio client:

```dart
VcrAdapter adapter = VcrAdapter();
Dio client = Dio();
client.httpClientAdapter = adapter;
```

After config the adapter, you now can use a cassette

```dart
adapter.useCassette('github/user_repos');

Response response = await client.get('https://api.github.com/users/trunghq3101/repos');
expect(response.statusCode, 200);
```

Now the request is stored in test/cassette/github/user_repos.json

If you have multiple requests for one test, they will be added in a list of requests
If de adapter can't find the right request, he will make a normal request and then store the request

This package is inspired by VCR gem

#### Next Features

- [ ] Work with Http Package
