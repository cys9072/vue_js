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

 


