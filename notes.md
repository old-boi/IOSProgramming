## Eğitime başlıyorum 13.07.2022

### 18.07.2022

#### Part 1

Spacer()
Divider()
Text()

CircleImage() koyduktan sonra offset ve padding ayarla 
.frame() -> sadece height ayarlarsan width'i otomatik ayarlıyor

.ignoresSafeArea(edges: .top, .bottom) vb kenar seçerek content'in safe area'ya taşmasını sağlıyorsun (sanırım padding'lerden dışa taşmasını sağlamak için kullanabiliyorum)

.font()
.foregroundColor()

vb. kullanabilirim

.offset(y: -130) gibi kullan, dene 
.padding(.bottom, -130) şeklinde dene

@State private var region = MK.... yaparak MapKit library'i de kullanarak Map gösterebiliyorum. 

VStack ve HStack kullanabilirim, vertical ve horizontal olarak componentları stackliyor bunlar. 

image koyduktan sonra .clipshape(Circle()) yazarak çember şeklinde kırptım. 
.shadow(radius: 7) gölge ekliyor

.overlay {
  Circle().stroke(.white, lineWidth: 4)
}

yaptığım zaman da Circle şeklinde, belirtilen özelliklerde çizim yapıyor. Bu durumda beyaz ve 4px kalınlığında bir çember çizdi.


.offset() is when we want to move a component from its auto-located position according to the order in which it is at on the VStack or HStack. 
.padding() is when we want there to be space between the default location of a component and other components. 


#### Part 2

Instead of hardcoding values, if we want to pull data from somewhere, i.e. a Landmark object, we can use 

var landmark_im: Image

and then pass the image while calling the struct somewhere else. 

Preview'da görmek için Image("Turtle_Rock") şeklinde hard code yapabiliriz. 

### Cannot use instance member 'coordinates' within property initializer; property initializers run before 'self' is available.

Bu yüzden .onAppear {} içinde region = setRegion() şeklinde kodumuzu çalıştırmamız gerekiyor. 

Group {} içine alınca içerideki her şeye aynı fonksiyonu uygulayabiliyorum.

ScrollView {}
.navigationTitle()
.navigationBarTitleDisplayMode(.inline) -> inline şekilde display ediyor


```swift
NavigationView {
            List(landmarks) { landmark in
                NavigationLink {
                    LandmarkDetail(landmark: landmark)
                } label: {
                    LandmarkRow(landmark_v: landmark)
                }
            }
            .navigationTitle("Landmarks")
        }
```

NavigationLink gideceği sayfayı, label nereye basıldığında bu sayfaya gidileceğini gösterir. 
Normalde List(landmarks, id: \.id) yapmam gerekiyordu ama Landmark struct'ı Identifiable protocol'e uygun olduğundan gerek kalmadı.


### Part 3

To give the user control over the list’s filter, you need to add a control that can alter the value of showFavoritesOnly. You do this by passing a binding to a toggle control.
A binding acts as a reference to a mutable state. When a user taps the toggle from off to on, and off again, the control uses the binding to update the view’s state accordingly.

```swift
Toggle(isOn: $showFavoritesOnly) {
                    Text("Show Favorites Only")
                }
```

@Published diyerek paylaştığımız @EnvironmentObject'ın değeri bundan sonra otomatik olarak update edilecek. 

ContentView  -> burada kullanmadığımız için hiçbir şey yazmıyorum. UPDATE: yazmayınca ContentView preview'u çöküyor. 
  LandmarkList  -> bu ve child view'larda kullanacağımız için önce @EnvironmentObject olarak property'i tanımladık. 
                -> .environmentObject() metoduyla da variable'ı ortama koyduk, child view'lara pass'ledik 
    LandmarkRow     -> objeyi kullanmam gerektiği zaman ModelData() olarak çağırıyorum ve ulaşıyorum, variable'a gerek yok
    LandmarkDetail  -> bu da aynı şekilde
    
    
Use the @StateObject attribute to initialize a model object for a given property only once during the life time of the app. This is true when you use the attribute in an app instance, as shown here, as well as when you use it in a view.


Eğer bir property, uygulama açıldıktan sonra tek bir defa initialize edilecekse @StateObject attribute'unu kullan.

Eğer environment object'i kullanmak istiyorsa ya ModelData() şeklidne çağıracak ya da @EnvironmentObject var x: ModelData() diyecek 
(tabii parent view'da .environmentObject(ModelData()) yazılmış olması lazım)


### Part 6 (4-5'i atladım)


