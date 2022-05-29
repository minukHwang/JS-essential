# API 가져와서 활용하는 법

<aside>
⚠️ 모든 API는 key 필요!!

</aside>

## Query String

<aside>
💡 주소?속성=값&속성=값&속성=값

</aside>

---

- 속성 → params 해당 API 마다 다 다름

### AXIOS

---

[https://github.com/axios/axios](https://github.com/axios/axios)

[시작하기](https://axios-http.com/kr/docs/intro)

1. `npm install axios`
2. `import axios form ‘axios’`
3. `axios.get('주소?속성=값&속성=값&속성=값')`
    1. https로 넣기!! 
4. .then(함수) 및 활용
    
    ```jsx
    import axios from "axios"
    
    function fetchMovies() {
        axios
            .get()
            .then(response => {
                console.log(response)
                const h1El = document.querySelector('h1')
                const imgEl = document.querySelector('img')
                h1El.textContent = response.data.Search[0].Title // 글자 넣기
                imgEl.src = response.data.Search[0].Poster // 그림 넣기
            })
    }
    ```