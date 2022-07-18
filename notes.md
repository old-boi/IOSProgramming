## Eğitime başlıyorum 13.07.2022

### 18.07.2022

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
