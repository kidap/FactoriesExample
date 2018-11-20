# Factory Example

## Code
```
//Model
struct Donut {
    var flavor: String
}

// Factories
// The factory pattern is a way to encapsulate the implementation details
// of creating objects, which adheres to a common base class or interface
struct MagicBoxDonutFactory {
    static func donut() -> Donut {
        return Donut(flavor: "cinnamon")
    }
}

struct CopsDonutFactory {
    static func donut() -> Donut {
        return Donut(flavor: "oreo")
    }
}

// DonutShop
struct DonutShop {
    var donutCreator: () -> Donut

    init(donutCreator: @escaping () -> Donut) {
        self.donutCreator = donutCreator
    }

    func getMeADonut() -> Donut {
        return donutCreator()
    }
}

// Using MagicBoxDonutFactory
let donutShop = DonutShop(donutCreator: MagicBoxDonutFactory.donut)
let donut1 = donutShop.getMeADonut()
print(donut1)
let donut2 = donutShop.getMeADonut()
print(donut2)

// Using CopsDonutFactory
let donut3 = DonutShop(donutCreator: CopsDonutFactory.donut).getMeADonut()
print(donut3)
```



## Output
```
Donut(flavor: "cinnamon")
Donut(flavor: "cinnamon")
Donut(flavor: "oreo")
```
