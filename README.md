#Rx Android

##### Rx Android는 Observable 객체가 던져주는 정보를 Observer가 subscribe하는 구조라고 생각하면 된다.

```Java
Observable<String> observable = Observable.create(new ObservableOnSubscribe<String>() {
    @Override
    public void subscribe(ObservableEmitter<String> emitter) throws Exception {
        for(int i=0; i<number.length; i++){
            emitter.onNext(number[i]);
            Thread.sleep(1000);
        }
        emitter.onComplete();
    }

});

observable.subscribeOn(Schedulers.io()).observeOn(AndroidSchedulers.mainThread()).subscribe(str -> {
    list.add(str);
    adapter.setDataAndRefresh(list);

});
}
```

