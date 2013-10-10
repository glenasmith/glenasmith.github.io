# Functional Java

---V

## Getting Functional with Guava

* Functional is so hot right now
* But are you sure you want to do this?
* The most abused part of Guava
* Warning! Will Robinson! Warning!

---V

## Functional Style

* Two main styles supported
* Predicates: filter all elements that match this criteria
* Functions: transform all elements of A into B


---V

## Predicates

* Iterables.filter(Iterable, Predicate), Maps.filter(Map, Predicate), etc
* Let's abuse it

```java
public List<People> findPeopleInPostcode(final int postCode) {
    return Lists.newArrayList(Iterables.filter(allPeople, Predicate<People>() {
        @Override
        public boolean apply(People person) {
            return person.getPostcode() == postCode;
        }
   });
}
```

---V

## Function

* Iterables.tranform(Iterable, Function), Collections2.transform, etc

```java
Collection<String> emails = Collections2.transform(allPeople, new Function<People, String>() {
    @Override
    public String apply(People person) {
      return person.getEmail();
    }
}
```

---V

## And once more...

* Are you sure you want to do this?
* Can often do the same thing in "native" Java which is more maintainable
 

