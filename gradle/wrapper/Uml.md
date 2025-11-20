---
marp: true
---

@startuml
!theme plain
skinparam componentStyle rectangle

package "UI Layer" {
  [Activity / Fragment] as View
}

package "ViewModel Layer" {
  [WheelsViewModel] as ViewModel
}

package "Data Layer" {
    [Repository] as Repo

    package "Data Sources" {
        [Remote Data Source] as RemoteDS
        [Local Data Source] as LocalDS
    }
}

package "External" {
    cloud "Remote API" as Api
    database "Room Database" as Db
}


View --> ViewModel : Notifie les événements utilisateur
ViewModel --> View : Expose les données (LiveData/StateFlow)

ViewModel --> Repo : Demande les données

Repo --> RemoteDS : Récupère les données distantes
Repo --> LocalDS : Récupère les données locales

RemoteDS --> Api : Appels réseau (HTTP)
LocalDS --> Db : Accès à la base de données (DAO)

@enduml
