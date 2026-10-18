## Необходимые классы
- MazeCell: ячейка в лабиринте, у которой есть границы
- Maze: лабиринт, состоящий из MazeCell ячеек
- MainWindow: главный класс, управляющий всеми компонентами программы
- UIWindow: отрисовка интерфейса

Дополнительно:
- CaveCell: ячейка в пещере, которая хранит только внутренее состояние
- Cave: пещера, состоящая из CaveCell ячеек

```plantuml

@startuml

abstract class ICell {
    - _is_free : bool
    + setState(state : int) : void
    {abstract} + status() : bool
}

class MazeCell {
    - _upper_wall : bool
    - _right_wall : bool
    + right() : bool&
    + upper() : bool&
}

class CaveCell {
}

class "BaseMap<T>" as BaseMap {
    # _height : int
    # _width : int
    # _multiple_cells : std::vector<T>
    + BaseMap(height : int, width : int)
    + height() : int
    + width() : int
}

class Maze
class Cave

ICell <|-- MazeCell
ICell <|-- CaveCell

Maze ..> BaseMap : T = MazeCell
Cave ..> BaseMap : T = CaveCell

@enduml

```