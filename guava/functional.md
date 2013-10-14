# Functional Java

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
List<Account> badPasswords = Lists.newArrayList(Iterables.filter(accounts, new Predicate<Account>() {
    @Override
    public boolean apply(Account account) {
        return account.getPassword().equals("pw");
    }
}));
```

---V

## Function

* Iterables.tranform(Iterable, Function), Collections2.transform, etc

```java
Collection<String> emails = Collections2.transform(accounts, new Function<Account, String>() {
    @Override
    public String apply(Account account) {
        return account.getEmail();
    }
});
```

---V

## And once more...

* Are you sure you want to do this?
* Can often do the same thing in "native" Java which is more maintainable
 

