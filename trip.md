```uml
@startuml
start

:日産レンタカー博多新幹線駅前店に朝9時に集合;
:レンタカーを借りて出発;
:昭和の街へ;
if(昼飯どうする？)then(パターン1)
:昭和の街で店に入る;
elseif then(パターン2)
:曇りです;
else(false)then(パターン3)
:昭和の街かパーキングエリアで
弁当を買って田染荘で食べる;
endif

end
@enduml
```
