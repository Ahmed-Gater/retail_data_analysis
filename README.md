A demo showing how to use Elasticsearch to analysis onlince store data


1. Rajouter le champs location de type geopoint avec une requete update et le scripting (chaque country est mappé à une région de francen e.g. United Kinngdom est mappé vers ile de france)
{
  "query": {
    "match": {
      "Country": "United Kingdom"
    }
  },
  "script": {
    "inline": "ctx._source.location = my_var; ctx._source.region='Ile de France'",
    "params": {
      "my_var": {
        "lat": 48.90851,
        "lon": 2.03403
      }
    }
  }
}
