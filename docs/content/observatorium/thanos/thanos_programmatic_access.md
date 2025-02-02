# Thanos Programmatic Access

The Thanos metrics can be queried using the [this](https://prometheus-api-client-python.readthedocs.io/) Python client library.
You can install the latest version with `pip install prometheus-api-client`.
You will need to extract the OpenShift bearer token for the client library to authenticate the [thanos](https://thanos-query-frontend-opf-observatorium.apps.smaug.na.operate-first.cloud/) instance.

## Personal token

You can use your personal token for testing and ad-hoc scripts, but it will expire in ~24 hours.

1. Login to https://console-openshift-console.apps.smaug.na.operate-first.cloud/ using `operate-first` login
2. Copy the token from the User dropdown menu
3. Use this token as your oauth bearer token when connecting to Thanos via the client library
   * Eg:
   ```python
   prometheus_api_client.prometheus_connect.PrometheusConnect(
     url='https://thanos-query-frontend-opf-observatorium.apps.smaug.na.operate-first.cloud',
     headers= {“Authorization”: “Bearer my_oauth_token_to_the_host”},
     disable_ssl=False
   )
   ```
4. The metric data can be extracted locally using the prometheus client in a Jupyter notebook
   * [Sample notebook](https://github.com/aicoe-aiops/time-series/blob/master/notebooks/ts-1-fetching-metrics.ipynb)
5. You can also spawn and run your notebooks on [JupyterHub](https://jupyterhub-opf-jupyterhub.apps.smaug.na.operate-first.cloud/)
