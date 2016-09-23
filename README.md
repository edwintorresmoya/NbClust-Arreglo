# NbClust-Arreglo


lista.methods = c("kl", "ch", "hartigan","mcclain", "gamma", "gplus",
                  "tau", "dunn", "sdindex", "sdbw", "cindex", "silhouette",
                  "ball","ptbiserial", "gap","frey")
lista.distance = c("metodo","euclidean", "maximum", "manhattan", "canberra")

tabla = as.data.frame(matrix(ncol = length(lista.distance), nrow = length(lista.methods)))
names(tabla) = lista.distance

for (j in 2:length(lista.distance)){
for(i in 1:length(lista.methods)){
    
    nb = NbClust(base_multi_sinna, distance = lista.distance[j],
                 min.nc = 2, max.nc = 10, 
                 method = "complete", index =lista.methods[i])
    tabla[i,j] = nb$Best.nc[1]
    tabla[i,1] = lista.methods[i]
    
}}

tabla
