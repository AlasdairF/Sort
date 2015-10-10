## Sort

Go's native Sort package uses interface elements, the reflection on which considerably slows down the sorting algorithms. Additionally descending order sorting using greater than for the `Less()` function is inefficient.

Herein are ascending and descending implemetations for native number types, with no reflection, less function calls and other optimizations.

Included are also key/value sorting algorithms and stable sorting.

### Example an ascending sort on slice of Ints

     import "github.com/AlasdairF/Sort/Int"
     list := []int{10, 44, 1, 7, 4, 0, -9, 0, 3, 65, 38}
     sortInt.Asc(list)
     
### Example a descending stable sort on slice of Uint32s

     import "github.com/AlasdairF/Sort/Uint32"
     list := []uint32{10, 44, 1, 7, 4, 0, 9, 0, 3, 65, 38}
     sortInt.StableDesc(list)

### Example sort on key/value pair Uint32/Float64

     import "github.com/AlasdairF/Sort/Uint32Float64"
     keyval := []sortUint32Float64.KeyVal{
         sortUint32Float64.KeyVal{0, 10.5},
         sortUint32Float64.KeyVal{1, 44.1},
         sortUint32Float64.KeyVal{2, 1.9},
         sortUint32Float64.KeyVal{3, 8.5},
     }
     sortUint32Float64.Desc(keyval)

### Example identical to above using the `New()` helper function

    import "github.com/AlasdairF/Sort/Uint32Float64"
     scores := []float64{10.5, 44.1, 1.9, 8.5}
     keyval := sortUint32Float64.New(scores) // keys are filled in automatically starting from 0
     sortUint32Float64.Desc(keyval)
     
     // Then the keyval underlying array can be reused as follows
     scores2 := []float64{5.4, 30.4, 100.5}
     keyval = sortUint32Float64.Fill(scores2, keyval)
     sortUint32Float64.Asc(keyval)
     
     // Maybe after the sorting you only want the indexes?
     keys := sortUint32Float64.Keys([]uint32{}, keyval)
