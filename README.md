
# React-w26

*1. Если в этом примере, изменить порядок Route таким образом:*
```
<Routes>
	<Route path="/" element={<Home />} />
	<Route path="/about" element={<About/>} />
	<Route path="/users" element={<Users />} />
</Routes>
```
То какой компонент будет отрисован по адресу /users? Объясните почему.

Последовательность, в которой перечислены  <Route> , не имеет значения, поэтому компонент Users

*2. Какое сообщение появится на экране по адресу http://localhost:3000/users/12345*

```
    ...
    <Route path='/users/:number' element={<User />} />
    ...

    function User(props) {
        const number = props.match.params.number;
        return(
            number===12345
                ? <h1>Моя личная страница</h1>
                : <h1>Страница пользователя {number}</h1>
        );
    }
```
Страница пользователя 12345

*3. Вспомните, какой второй параметр принимает метод map*

*второй параметр - index

4. Как бы вы подошли к решению задачи по выводу компонентом <CardList> только тех экземпляров компонента <Card>, цена которых не превышает заданную?*
```
function CardList () {
     shoes.map((item,index)=> {return (item.price < 100?        
<Card
key={index}
id={item.id}
title={item.title}
{shoes.filter(item => item.price <= '99').map(filterprice => {                 {filterprice.price}})}
)})
description={item.description}
imgLink={item.imgLink}
/> }

 ```
*5. Как задать параметр в пути? Например, *filter (*`useLocation, useSearchParams`*)*
```
function myFunction() {
  const History = useHistory();
  function handleClick(filter) {
      history.push(`/name?filter=${filter}`);
  }  
  const location = useLocation();
  const useParams = new URLSearchParams(location.search);

  return (
    <div>
      <p>Type: {useParams.get("type") 
      onChange={handleClick("name")}}</p>
      <p>Name: {useParams.get("name")
      onChange={handleClick("name")}
      }</p>
    </div>
  )
}
```

*6. Какая разница между element и children в указании роутера?*

children будет всегда отображаться  - независимо от того сопоставляется ли path или нет

*7. Зачем нужен `exact`?*

свойство exact устанавливается в компонент Route для строгой проверки адресов

*8. Cамостоятельно разберитесь, зачем нужны `useMatch`, `useLocation`, `useNavigate`?*

useMatch - возвращает данные о маршруте по заданному пути относительно текущего местоположения
useLocation- хук возвращает объект текущего location
useNavigate - возвращает функцию, которая позволяет программно перемещаться

*9. Как можно сделать перенаправление на другую страницу по клику на кнопку с помощью useNavigate?
Ищите ответ в документации к react-router-dom*

``` import React from "react";
import { useNavigate } from "react-router-dom";
export default const About = () => {
  let navigate = useNavigate();
  const goHome = () => {
    navigate("/");
  };
  return (
    <div>
      <h1>About page here!</h1>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugit, modi!
      </p>
      <button onClick={goHome}>Go to home page</button>
    </div>
  );
};
```
