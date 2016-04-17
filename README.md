# ymaps
ymaps.ready(init);

function init() {
    // Создаем карту.
    var cLat = 59.950228865687365;
    var cLon = 30.31613831336122;
    var mCenter = [cLat, cLon];
    var myMap = new ymaps.Map("map", {
            center: mCenter,
            zoom: 8
        }, {
            searchControlProvider: 'yandex#search'
        });
    var myCollection = new ymaps.GeoObjectCollection();
    // Создаем ломаную, используя класс GeoObject.
    myCollection.add(new ymaps.GeoObject({geometry: {type: "LineString", coordinates: [mCenter,[cLat,31.05]]}})); // право
    myCollection.add(new ymaps.GeoObject({geometry: {type: "LineString", coordinates: [mCenter,[cLat,29.05]]}})); // лево
    
    myCollection.add(new ymaps.GeoObject({geometry: {type: "LineString", coordinates: [mCenter,[59.5,cLon]]}})); // низ
    myCollection.add(new ymaps.GeoObject({geometry: {type: "LineString", coordinates: [mCenter,[60.5,cLon]]}})); //верх

    // Добавляем линии на карту.
    myMap.geoObjects
        .add(myCollection)
}
