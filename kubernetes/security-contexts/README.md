# Security Contexts

## Gather pod and container security contexts 

Kubectl, go template:

```
kubectl get pods --insecure-skip-tls-verify -o go-template --template='{{range .items}}{{"pod: "}}{{.metadata.name}}                                                                                                                 1 ⨯
    {{if .spec.securityContext}}
      PodSecurityContext:                                     
        {{"runAsGroup: "}}{{.spec.securityContext.runAsGroup}}    
        {{"runAsNonRoot: "}}{{.spec.securityContext.runAsNonRoot}}                                                                      
        {{"runAsUser: "}}{{.spec.securityContext.runAsUser}}                                 {{if .spec.securityContext.seLinuxOptions}}
        {{"seLinuxOptions: "}}{{.spec.securityContext.seLinuxOptions}}                       {{end}}
    {{else}}PodSecurity Context is not set
    {{end}}{{range .spec.containers}}
    {{"container name: "}}{{.name}}               
    {{"image: "}}{{.image}}{{if .securityContext}}                                                                          
        {{"allowPrivilegeEscalation: "}}{{.securityContext.allowPrivilegeEscalation}}   {{if .securityContext.capabilities}}
        {{"capabilities: "}}{{.securityContext.capabilities}}                           {{end}}                          
        {{"privileged: "}}{{.securityContext.privileged}}                               {{if .securityContext.procMount}}
        {{"procMount: "}}{{.securityContext.procMount}}                                 {{end}}
        {{"readOnlyRootFilesystem: "}}{{.securityContext.readOnlyRootFilesystem}}
        {{"runAsGroup: "}}{{.securityContext.runAsGroup}}    
        {{"runAsNonRoot: "}}{{.securityContext.runAsNonRoot}}                                                                 
        {{"runAsUser: "}}{{.securityContext.runAsUser}}                                 {{if .securityContext.seLinuxOptions}}       
        {{"seLinuxOptions: "}}{{.securityContext.seLinuxOptions}}                       {{end}}{{if .securityContext.windowsOptions}}
        {{"windowsOptions: "}}{{.securityContext.windowsOptions}}                       {{end}}
    {{else}}                      
        SecurityContext is not set
    {{end}}                                 
{{end}}{{end}}' > kubectl-get-seccontext.txt

```

{% hint style="info" %}
 Super-powers are granted randomly so please submit an issue if you're not happy with yours.
{% endhint %}

Once you're strong enough, save the world:

{% code title="hello.sh" %}
```bash
# Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```
{% endcode %}



