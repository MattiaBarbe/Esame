----------------------------------------------------------
Esempio DAO
----------------------------------------------------------
@staticmethod
    def getArchi(anno):
        conn = DBConnect.get_connection()
        cursor = conn.cursor(dictionary=True)
        
        query = '''select r1.driverId as id1,r2.driverId as id2,count(distinct(r1.raceId)) as vittorie from results r1, results r2,races c1,races c2 
        where c1.`year`=%s and c2.`year`=%s and
        r1.raceId =c1.raceId and r2.raceId =c2.raceId and
        r1.driverId !=r2.driverId and r1.`position` >0 and r2.position>0 and
        r1.raceId=r2.raceId and r1.`position` <r2.`position`
        group by r1.driverId,r2.driverId order by r1.driverId,r2.driverId'''
        
        cursor.execute(query,(anno,anno,))
        archi=[]
        nodi=[]
        for row in cursor:
            archi.append(row)
            if row["id1"] not in nodi:
                nodi.append(row["id1"])
            if row["id2"] not in nodi:
                nodi.append(row["id2"])
        cursor.close()
        conn.close()
        return archi,nodi

if __name__=="__main__":
    dao=DAO()
    print(dao.getArchi(1951))
    #risultato.append(Pilota(**row))
--------------------------------------------------------
Esempio classe
--------------------------------------------------------
from dataclasses import dataclass

@dataclass
class Pilota():
    driverId:int
    driverRef:str
    vettore:[] --> posso non metterlo nell'inizializzazione
    
    def __eq__(self,other):
        return self.driverId == other.driverId
    def __hash__(self):
        return hash(self.driverId)
    def __str__(self):
        return self.driverRef
--------------------------------------------------------
Esempio random
--------------------------------------------------------
#ciclare sugli archi con il peso
for arco in self.grafo.edges(data=True):
    #arco.....

#IDMAP!!!
self.idMap={}
for nodi in boh:
self.idMap[nodi.id]=nodi

#aggiungere elementi dropDown
self._view.dd.options=[]
self._view.dd.options.append(ft.dropdown.Option(key="valore nascosto",text="valore visivo"))

#aggiungere a stampa
self._view.txtresult.controls=[]
self._view.txtresult.controls.append(ft.Text(f'{variabile} ciao'))

#ordinamento
diz={}
        for nodo in self.grafo.nodes():
            diz[nodo]=0
            for vicino in self.grafo.neighbors(nodo):
                diz[nodo]+=self.grafo[nodo][vicino]["weight"]

        ordinato=sorted(diz,key=lambda x:diz[x], reverse=True)
        ordinato=ordinato[0:6]
        return ordinato,diz
#datediff per differenza date database
#unique

#per classe con data
from datetime import datetime
    data:datetime

--------------------------------------------------------
Esempio Ricorsione
--------------------------------------------------------
 def team(self,k):
    self.bestTeam = None
    self.bestScore = 99999
    self.ricorsione([],k)
    return self.bestTeam,self.bestScore
 
 def ricorsione(self,parziale,k):
        if len(parziale)==k:
            tasso=0
            for n in copy.deepcopy(parziale):
                for p in self.grafo.predecessors(n):
                    if p not in parziale:
                        tasso+=self.grafo[p][n]["peso"]
                if tasso<self.bestScore:
                    self.bestScore=tasso
                    self.bestTeam=copy.deepcopy(parziale)
        else:
            possibili=self.successori(parziale,k)
            for p in possibili:
                parziale.append(p)
                self.ricorsione(parziale,k)
                parziale.pop()

    def successori(self,parziale,k):
        res=[]
        if len(parziale)==0:
            res=self.grafo.nodes()
        else:
            if len(parziale)<k:
                for n in self.grafo.nodes():
                    if n not in parziale:
                        res.append(n)
        return res

--------------------------------------------------------
Esempio Componenti connesse
--------------------------------------------------------
import networkx as nx

grafo=nx.Graph()
nodi=[1,2,3,4,5]
grafo.add_nodes_from(nodi)
grafo.add_edge(1,2)
grafo.add_edge(2,3)
grafo.add_edge(4,5)
print(grafo)
connesse=nx.node_connected_component(grafo,1)
conn=nx.connected_components(grafo)
numc=nx.number_connected_components(grafo)
print(connesse)

#orientato
nodi=[1,2,3,4,5]
grafo2=nx.DiGraph()
grafo2.add_nodes_from(nodi)
grafo2.add_edge(1,2)
grafo2.add_edge(2,3)
grafo2.add_edge(3,1)
grafo2.add_edge(4,5)
print(grafo2)
connesse=nx.strongly_connected_components(grafo2)
num=nx.number_strongly_connected_components(grafo2)
print(num)
cd=nx.weakly_connected_components(grafo2)
for c in cd:
    print(c)
for c in connesse:
    print(c)

connesse1=nx.strongly_connected_components(grafo2)
salva=None
for c in connesse1:
    if 1 in c:
        salva = c
    #componenti connesse al nodo
print(salva)
    

















