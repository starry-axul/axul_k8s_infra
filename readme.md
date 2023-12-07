# Setup

creating a templates/axul-contact-secret.yaml file with the values:
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: {{ .Release.Name }}-{{.Values.contact.name}}-secret
  namespace: {{ .Release.Name}}
type: Opaque
data:
  DATABASE_HOST: {{"[value]" | toString | b64enc }}
  DATABASE_PORT: {{"[value]" | toString | b64enc }}
  DATABASE_NAME: {{"[value]" | toString | b64enc }}
  DATABASE_USER: {{"[value]" | toString | b64enc }}
  DATABASE_PASSWORD: {{"[value]"  | toString | b64enc }}
  TOKEN: {{"[value]" | toString | b64enc }}
  BIRTHDAY_PAGE: {{"[value]" | toString | b64enc }}
  PUSH_URL: {{"[value]" | toString | b64enc }}
```

and execute 
```sh
helm install axul .
```