= Go lang memo
// See https://hubpress.gitbooks.io/hubpress-knowledgebase/content/ for information about the parameters.
// :hp-image: /covers/cover.png
:published_at: 2017-10-27
// :hp-tags: HubPress, Blog, Open_Source,
// :hp-alt-title: My English Title

Eg of basic program

[source, go]
----
package main

import "fmt"
/*import (
	"fmt"
    "math"
)*/

func add(x int, y int) int {
	return (x + y)
}

func multipl(a int, b int) int {
	return (a*b)
}

func main() {
	fmt.Println(add(42, 13))
	fmt.Println(multipl(64, 96))
}
----