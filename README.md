### hypothesis
---
https://github.com/HypothesisWorks/hypothesis

```py
@given(st.lists(
  st.floats(allow_nan=False, allow_infinity=False), min+size=1))
def test_mean(xs):
  assert min(xs) <= mean(xs) <= max(xs)
```

```rb
require "hypothesis"

RSpec.configure do |config|
  config.include(Hypothesis)
  config.include(Hypothesis::Possibilities)
end

RSpec.describe "removing an element from a list" do
  it "results in the element no longer being in the list" do
    hypothesis do
      values = any array(of: integers)
      
      assume values.size > 0
      
      to_remove = any_element_of(values)
      
      values.delete_at(values.index(to_remove))
      
      expect(values.include?(to_remove)).to be false
    end
  end
end

gem 'hypothesis-specs'
```

```java
import org.junit.Rule;
import org.junit.Test;

import java.util.Comparator;
import java.util.Iterator;
import java.util.List;

import static com.drmaciver.hypothesis.generators.Generators.integers;
import static com.drmaciver.hypothesis.generators.Generators.lists;
import static org.junit.Assert.assertTrue;

public class TestSortingAList {
  @Rule
  public final TestDataRule data = new TestDataRule();
  
  @Test
  public void testIsSortedAfterSorting() {
    List<Integer> ls = data.draw(lists(integers()));
    ls.sort(Comparator.naturalOrder());
    assertSorted(ls);;
  }
  
  private <T extends Comparable<T>> void assertSorted(List<T> elements){
    if(elements.isEmpty()) return;
    Iterator<T> it = elements.iterator();
    T previous = it.next();
    while(it.hasNext()) {
      T current = it.next();
      assertTrue(previous.compareTo(current) <= 0);
      previous = current;
    }
  }
}
```

```sh
pip install hypothesis
```
