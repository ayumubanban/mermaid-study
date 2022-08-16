[mermaid で描く - UML とか AWS 構成図とかを描くツール](https://zenn.dev/ibaraki/articles/522797d7f6b4c1#mermaid%E3%81%A7%E6%8F%8F%E3%81%8F)

```mermaid
graph TB
    A[Hard edge] -->|Link text| B(Round edge)
    B --> C{Decision}
    C -->|One| D[Result one]
    C -->|Two| E[Result two]
```

[GitHub で使えるようになった Mermaid の便利なところ](https://zenn.dev/yasuhiroki/articles/dd0feae790ba41)

```mermaid
flowchart LR
  いのき --> ボンバイエ ---> いのき --> いのき
```

```mermaid
flowchart LR
  ヒロインA & ヒロインB --> 主人公
```

```mermaid
flowchart TD
  START-->A{アントニオ?}
  A-->|Yes|猪木
  A-->|No|B{アントキノ?}
    B-->|Yes|猪木
    B-->|No|END
```

スタートは ●、エンドは ◉ ではないのか？ ← [始点終点にこの 2 記号を使うのは、あくまで State Machine Diagram での話なのかもねぇ](https://mermaid-js.github.io/mermaid/#/flowchart)

```mermaid
flowchart TB
  %% START[●] --> END[◉] ← こうだと、描画されないなぁ…
  START[START] --> END[END]
```

↑ PlantUML だと、 スタートは ●、エンドは ◉ ということになってる。
https://plantuml.com/ja/activity-diagram-beta
IT 専科の説明の方でも。
https://www.itsenka.com/contents/development/uml/activity.html

https://mermaid-js.github.io/mermaid/#/flowchart

```mermaid
flowchart LR
    id1[This is the text in the box]
    id2(This is the text in the box)
    id3([This is the text in the box])
    id4{This is the text in the box}
    id5[/Christmas\]
    id6[\Go shopping/]
```

```mermaid
flowchart LR
  A --> B
  A --- B
  A -- This is the text! --- B
  A -- This is the text! --> B
  A --- |This is the text| B
  A --> |This is the text| B
```

> Each node in the flowchart is ultimately assigned to a rank in the rendered graph, i.e. to a vertical or horizontal level (depending on the flowchart orientation), based on the nodes to which it is linked.

> For dotted or thick links, the characters to add are equals signs or dots

```mermaid
flowchart TB
  A[Start] --> B{Is it?}
  B -- Yes --> C[OK]
  C --> D[Rethink]
  D --> B
  B -- No ----> E[End]
```

```mermaid
flowchart LR
  id1["This is the (text) in the box"]
```

```mermaid
flowchart LR
  A["A double quote:#quot;"] -->B["A dec char:#9829;"]
```

```mermaid
flowchart TB
  c1-->a2
  subgraph ide1[one]
    a1-->a2
  end
  subgraph two
    b1-->b2
  end
  subgraph three
    c1-->c2
  end
```

```mermaid
flowchart TB
  c1-->a2
  subgraph one
    a1-->a2
  end
  subgraph two
    b1-->b2
  end
  subgraph three
    c1-->c2
  end

  one --> two
  three --> two
  two --> c2
```

```mermaid
flowchart LR
  subgraph TOP
    direction TB
    subgraph B1
      direction RL
      i1 --> f1
    end
    subgraph B2
      direction BT
      i2 --> f2
    end
  end

  A --> TOP --> B
  B1 --> B2
```

fontawesome は、さすがにサラの状態では使えないか

```mermaid
flowchart TB
  B["fab:fa-twitter for peace"]
  B --> C[fa:fa-ban forbidden]
  B --> D(fa:fa-spinner);
  B --> E(A fa:fa-camera-retro perhaps?)
```
