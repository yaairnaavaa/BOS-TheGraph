# BOS + TheGraph

This repository is an example for the implementation of The Graph, a decentralized protocol that allows indexing and querying blockchain data.

In this case its implementation with BOS consists of retrieving the NFTs listed in a Marketplace whose information is indexed in TheGraph.

![NFTs](https://drive.google.com/uc?id=1g_8K90qRKjCGZeenBwYnYbzbTXbmKdo3)

## How to implement TheGraph in BOS?

```
useEffect(() => {
  var query = `query {
                        tokens{
                                id
                                title
                                owner_id
                                media
                                owner_id
                            }
                        }`;

  asyncFetch("https://api.thegraph.com/subgraphs/name/devscloudmex/nativonft", {
    method: "POST",
    headers: {
      "content-type": "application/json",
    },
    body: JSON.stringify({
      query: query,
    }),
  })
    .then(({ body }) => {
      setNFTData(body.data.tokens);
    })
    .catch((err) => console.log(err));
}, []);
```
