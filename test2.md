```uml
@startuml
start
お客 -> ホール係 -> 厨房: Authentication Request
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: another authentication Response
end
@enduml
```
