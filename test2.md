```uml
@startuml
start
お客 -> ホール係: Authentication Request
ホール係 -> 厨房
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: another authentication Response
end
@enduml
```
