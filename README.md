# BOS + TheGraph

This repository is an example for the implementation of The Graph, a decentralized protocol that allows indexing and querying blockchain data.

In this case its implementation with BOS consists of retrieving the NFTs listed in a Marketplace whose information is indexed in TheGraph.

![NFTs](https://drive.google.com/uc?id=1g_8K90qRKjCGZeenBwYnYbzbTXbmKdo3)

## How to implement TheGraph in BOS?

Making queries to The Graph is very simple, we only have to make a call from BOS to the API using asyncFetch to the URL of the subgraph that contains the information.

In the following example we will use the following subgraph: https://thegraph.com/hosted-service/subgraph/devscloudmex/nativonft

Finally we must send the query with the parameters that we want to obtain from the subgraph, in the previous link we can generate the queries to test and add them in the API query in BOS.

![TheGraph](https://drive.google.com/uc?id=10gTvJH3Idnc8JFucFG3upmygVYN0bpMr)

Example:
```jsx
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

BOS Widget: https://near.social/owa-is-bos.near/widget/BOS-TheGraph
