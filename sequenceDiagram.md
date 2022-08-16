[GitHub で使えるようになった Mermaid の便利なところ](https://zenn.dev/yasuhiroki/articles/dd0feae790ba41)

```mermaid
sequenceDiagram
  autonumber
  Client->>+Server: Get /issues
  Server-->>-Client: response
```

```mermaid
sequenceDiagram
  autonumber
  actor Client
  Client->>+Server: GET /issues
  Server--)Server2: 非同期リクエスト
  Server-->>-Client: response
  loop
    Server2-->Server2: なにかしら
    Note right of Server2: 処理が完了しなくても<br />10秒で強制終了する
  end
```

https://mermaid-js.github.io/mermaid/#/sequenceDiagram

```mermaid
sequenceDiagram
  %% participant Alice
  actor A as Alice
  %% participant Bob
  participant John

  %% Alice ->> John: Hello John, how are you?
  %% John -->> Alice: Great!
  %% Alice -) John: See you later!
  A ->> John: Hello John, how are you?
  John -->> A: Great!
  A -) John: See you later!
```

```mermaid
sequenceDiagram
  %% Alice ->> John: Hello John, how are you?
  %% activate John
  %% John -->> Alice: Great!
  %% deactivate John

  Alice ->>+ John: Hello John, how are you?
  John -->>- Alice: Great!
```

```mermaid
sequenceDiagram
  Alice ->>+ John: Hello John, how are you?
  Alice ->>+ John: John, can you hear me?
  John -->>- Alice: Hi Alice, I can hear you!
  %% John ->>+ John: hoge ->>- John: huga
  John ->> John: hoge
  John -->>- Alice: I feel great!

  %% John ->>+ John: hoge ->>- John: huga
  John ->>+ John: foo
  John -->>- John: baz
```

```mermaid
sequenceDiagram
  Alice -> John: Hello John, how are you?
  Note over Alice,John: A typical interaction
  Note over Alice: AliAli
  Note right of John: Text in note
```

```mermaid
sequenceDiagram
  Alice ->> John: Hello John, how are you?
  loop Every minute
    John -->> Alice: Great!
  end
```

```mermaid
sequenceDiagram
  Alice ->> Bob: Hello Bob, how are you?
  alt is sick
    Bob ->> Alice: Not so good :(
  else is well
    Bob ->> Alice: Feeling fresh like a daisy
  end
  opt Extra response
    Bob ->> Alice: Thanks for asking
  end
```

```mermaid
sequenceDiagram
  Consumer -->> API: Book something
  API -->> BookingService: Start booking process
  break when the booking process fails
    API -->> Consumer: show failure
  end
  API -->> BillingService: Start billing process
```

```mermaid
sequenceDiagram
  participant Alice
  participant John

  rect rgb(50, 250, 255)
    note right of Alice: Alice calls John.
    Alice ->>+ John: Hello Johm, how are you?
    rect rgb(200, 150, 255)
      Alice ->>+ John: John, can you hear me?
      John -->>- Alice: Hi Alice, I can hear you!
    end
    John -->>- Alice: I feel great!
  end

  Alice ->>+ John: Did you want to go to the game tonight?
  John -->>- Alice: Yeah! See you there.
```

```mermaid
sequenceDiagram
  autonumber
  Alice ->> John: Hello John, how are you?
  loop Healthcheck
    John ->> John: Fight against hypochondria
  end
  Note right of John: Rational thoughts!
  John -->> Alice: Great!
  John ->> Bob: How about you?
  Bob -->> John: Jolly good!
```

https://mermaid-js.github.io/mermaid/#/examples?id=sequence-diagram-blogging-app-service-communication

```mermaid
sequenceDiagram
  participant web as Web Browser
  participant blog as Blog Service
  participant account as Account Service
  participant mail as Mail Service
  participant db as Storage

  Note over web, db: The user must be logged in to submit blog posts

  web ->>+ account: Logs in using credentials
  account ->>+ db: Query stored accounts
  db ->>- account: Respond with query result

  alt Credentials not found
    account ->> web: Invalid credentials
  else Credentials found
    account ->>- web: Successfully logged in

    Note over web, db: When the user is authenticated, they can now submit new posts

    web ->>+ blog: Submit new post
    blog ->> db: Store post data

    par Notifications
      blog --) mail: Send mail to blog subscribers
      blog --) db: Store in-site notifications
    and Response
      blog -->>- web: Successfully posted
    end
  end
```
