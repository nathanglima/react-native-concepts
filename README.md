<img alt="GoStack" src="https://camo.githubusercontent.com/a869a2aaab296ef925343d7e76518cd213eb0a30/68747470733a2f2f73746f726167652e676f6f676c65617069732e636f6d2f676f6c64656e2d77696e642f626f6f7463616d702d676f737461636b2f6865616465722d6465736166696f732d6e65772e706e67" />

<h2 align="center">
  Challenge 03: React Native concepts
</h2>


## :page_facing_up: About this challenge

The objective of this challenge is to apply the knowledge acquired in React Native, This case we developed the front-end of the mobile application, consuming our API previously developed and necessary was a list our repositories and for each repository must be a button for to give a likes on the repository.

We went to challenge the develop a following items: List the repositories of your API and like one of the repositories retrieve by the API.

## :rocket: About of tests
Some rules for evaluating this challenge were proposed, some tests were written using jest and to pass the tests it is necessary to respect all the points below:

#### *should add a like to the like counter of the repository*

In order for this test to pass, your application must be able to add a like in one of the listed repositories by clicking on the 'Like' button and that update should be viewed on the screen.

```js
const [repositories, setRepository] = useState([]);
```

```js
useEffect(() => {
  api.get('repositories').then(response => {
    setRepositories(response.data);
  });
}, []);
```

```js
async function handleLikeRepository(id) {

  const response = await api.post(`repositories/${id}/like`);
  
  const likedRepository = response.data;

  const repositoriesUpdated = repositories.map(repository => {
    if(repository.id == id) {
      return likedRepository;
    } else {
      return repository;
    }
  });

  setRepositories(repositoriesUpdated);
}
```

```js
<TouchableOpacity
  style={styles.button}
  onPress={() => handleLikeRepository(repository.id)}
  testID={`like-button-${repository.id}`}
>
  <Text style={styles.buttonText}>Curtir</Text>
</TouchableOpacity>
```
