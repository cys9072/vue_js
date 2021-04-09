# vue_js
vue_js 개념,문법 정리 공부

🔴 vue_js는 기본적인 html css js의 기본수준이 중간레벨을 하는정도로 기준을 잡고 시작해야함. 그래서 기본적인 문법만 아는 본인은 js복습겸 심화학습을 병행 하면서 공부할예정. 
🔴 유튜브나 기타 다른 기초강의를 찾아봤으나 일단 vue_js공식사이트에서 제공하는 https://www.vuemastery.com/courses/intro-to-vue-js/vue-instance/ 에서 기본적인 학습을 한후에 다시 
    한국어 강의를 들을예정. 영어를 그렇게 잘하는건 아님.. 영어자막을 켜놓고 모르는 단어가 나오면 그때그때 찾아서 해결해 볼예정. 100%흡수보단 50%까지만 흡수하자고 생각하고 공부
   🟢총 10개 강의이며 하루만에 다 볼수 있을듯함. 2021.04.06 첫 시작.
   
🔴 설치 및 스크립트 넣는 법은 구글링해서 간단히 나오니 따로 설명 x

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
1️⃣<<The Vue Instance>>
  
<body>
    <div id="app">
        <h1>{{ product }}</h1>
      
        //product라는 벨류의값이 h1태그안에 pull됨 중복 중괄호 안에 property를 넣으면 value값을 도출,표현식(Expression) 이라고 부른다
        안에들어가는것들은 연산자도 가능 하고 , 함수, 넘버 모두 가능함
        vue 는 Reactive 해서 프로퍼티 벨류가 바뀌면 그에따라 바로 Expression안의 값이 바뀐다. 즉 어디든 linked 되있다고 생각하면 되고,
        중복되어있는 Expression도 모두 값이 바뀐다. 
        console에서 app.product ='홀롤롤ㄹ'라고 바꾸면 즉시 html에서도 바뀌는걸 볼 수가 있다
        
    </div>
    <script>
                      //->새로운 vue instance 생성, 안에는 데이터를 저장하고 작업을 수행되는데 사용됨.
        var app = new Vue({ 
        
            el: '#app',   
                     //-> app이라고 불리는 요소속성을 만듦, 
                    instance가 div id="app"과 plugged in 됨,instance와 dom 사이에 관계를 짓기위해 el이라는요소를 사용해서 연결을 해줌
            
            data: { 
                    //instance는 data에 대한 속성을 가질수 있고 이름은 사용자가 정할수 있다.
                product: 'Socks' //product라는 property를 가지고 value는 'Socks'
            },
        })
    </script>
</body>

정리 ->
  
the Vue instance is the heart of the application.
뷰는 어플리케이션에 핵심이고

It plugs in to an element in the DOM,and that element can use an expression
DOM요소에 연결되며 해당 요소는 표현식(expression)을 사용하여 instance의 data를 표시 할 수 있다

https://www.vuemastery.com/courses/intro-to-vue-js/vue-instance


2️⃣<<Attribute Binding>>
  <body>
    <div id="app">
        <div class="product-image">
          
            //v-bind는 데이터와 속성사이를 동적으로 바인딩 해줌, 이떄 속성을 바인딩할때는 {{}}아닌 " " 사이에 property를 넣어줌
            많이 사용하는 문법인데 v-bind: 대신 : 으로 대체 가능
            ex)
            v-bind:src="image" = :src="image"
            v-bind:href="url" = :href="url"
            v-bind:class="isActive" = :class="isActive"

            <img v-bind:src="image" alt="">
        </div>
        <div class="product-info">
            <h1>{{ product }}</h1>
        </div>
    </div>
    <script>
        var app = new Vue({
            el: '#app',
            data: {
                product: 'Socks',
                image: '이미지주소'
            },
        })
    </script>
</body>

  정리 ->
Data can be bound to HTML attributes.
 데이터는 HTML속성에 바인딩 될 수 있다
Syntax is v-bind: or : for short.
 문법은 :로 대체될수 있다
The attribute name that comes after the : specifies the attribute we’re binding data to.
 :뒤에오는 속성은 데이터를 바인딩할 속성을 지정하면됨 ""사용해서
Inside the attribute’s quotes, we reference the data we’re binding to.
 ""안에 속성은 데이터의 바인딩을 참조함



3️⃣<<Conditional Rendering>>
<body>
    <div id="app">
        <div class="product-image">

            <img v-bind:src="image" alt="">
        </div>
        <div class="product-info">
            <h1>{{ product }}</h1>
            <p v-if="stock > 10">재고있음</p>
            요소의 값으로 조건부를 정해서 true이면 보이고 false이면 요소를 dom에서 삭제한다.
            요소와 조건식을 같이 쓸수 있다.
            <p v-else-if="stock <=8 && stock > 7">재고8개있음</p>
            <p v-else>재고없음</p>

            <p v-show="stock">쑈우</p>
            참일때 보이고 거짓일때 안보이는것 if문과 같지만 DOM에서는 css로 display:none을 준다. 
            즉 요소가 삭제 되는게 아니라 보이지만 않게 하는것
        </div>
    </div>
    <script>
        var app = new Vue({
            el: '#app',

            data: {
                product: 'Socks',
                image: '이미지주소',
                stock: 0,
            },
        });
    </script>
</body>
정리 ->
조건부 렌더링을 사용할수 있다
v-if
v-else-if
v-else
v-show

If whatever is inside the directive’s quotes is truthy, the element will display.
따옴표에 지시문이 진실이면 요소가 표시됨
You can use expressions inside the directive’s quotes.
지시문의 따옴표안에 표현식을 사용할 수 있다.
V-show only toggles visibility, it does not insert or remove the element from the DOM.
show는 가시성을 전환 할 뿐이고, DOM에서 요소를 삭제/추가 하지  

하.... 6강까지 봤는데.. 다 날라갔다 자료... 다시 하자,....

4️⃣<<list Rendering>>
    <body>
    <div id="app">
        <div class="product-image">

            <img v-bind:src="image" alt="" style="width:100px;">
        </div>
        <div class="product-info">
            <h1>{{ product }}</h1>
            <p v-if="inStock">재고있음</p>
            <p v-else>재고없음</p>

            <ul>
                <li v-for="detail in details">{{detail}}</li>
                <!-- A in As 라는 표현식이고 v-for라는 표현식은 반복해준다.
                A는 As라는 객체의 별명 또는 닉네임이다. 즉 As의 객체가 A로 들어간다
                이떄 As를 컬렉션 이라고도 부른다
                그래서 중복 중괄호안에 A를 써서 문자열을 반복 할 수 있다. -->
            </ul>

            <div v-for="varient in varients" v-bind:key="varient.varientId">
                이렇게 반복을 쓸때 특수 key 속성을 사용하여 vue는 각각의 노드의 id를 추적할수 있게 만듭니다. 
                여기서는 key를 varient.varientId 에 바인딩 합니다
                <p>{{varient.varientTech}}</p>
            </div>
        </div>
    </div>
    <script>
        var app = new Vue({
            el: '#app',
            data: {
                product: '나루토',
                image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/c/c9/Naruto_logo.svg/1024px-Naruto_logo.svg.png',
                inStock: true,
                details: ['나루토', '사스케', '카카시'],

                varients: [{
                        varientId: 2234,
                        varientTech: "나선한"
                    },
                    {
                        varientId: 2235,
                        varientTech: "치도리"
                    }
                ]
            }
        });
    </script>
</body>

정리->
The v-for directive allows us to iterate over an array to display data.
v-for 지시문을 사용하면 배열을 반복하여 데이터를 표시 할 수 있다.

We use an alias for the element in the array being iterated on, and specify the name of the array we are looping through. Ex: v-for="item in items"
반복되는 배열의 요소에 별명을 사용하고, 반복되는 배열의 이름으로 저장함. ex> v-for = A in As

We can loop over an array of objects and use dot notation to display values from the objects.
객체의 배열을 반복할수 있고, 점 표기법을 사용해서 객체의 값을 표시 할 수 있다.

When using v-for it is recommended to give each rendered element its own unique key.
v-for를 사용할 때 렌더링된 각 요소에 고유한 키를 제공하는걸 매우매우 추천함

