---
title: 'TN055 : Migration d’Applications de classe de base de données de ODBC MFC vers les Classes DAO MFC'
ms.date: 06/20/2018
helpviewer_keywords:
- DAO [MFC], migration
- TN055
- migration [MFC], ODBC database applications
- ODBC classes [MFC], DAO classes
- migrating ODBC database applications [MFC]
- porting database applications to DAO
- ODBC [MFC], DAO
- porting ODBC database applications to DAO
- migrating database applications [MFC]
ms.assetid: 0f858bd1-e168-4e2e-bcd1-8debd82856e4
ms.openlocfilehash: 7a1d3436a9b19c40df2a08576d797de49833f14f
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611232"
---
# <a name="tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes"></a>TN055 : Migration d’Applications de classe de base de données de ODBC MFC vers les Classes DAO MFC

> [!NOTE]
> Les Assistants et l’environnement Visual C++ ne prennent pas en charge les DAO (bien que les classes DAO sont incluses et vous pouvez toujours les utiliser). Microsoft recommande d’utiliser [modèles OLE DB](../data/oledb/ole-db-templates.md) ou [ODBC et MFC](../data/odbc/odbc-and-mfc.md) pour les nouveaux projets. Vous devez uniquement utiliser DAO à la gestion des applications existantes.

## <a name="overview"></a>Vue d'ensemble

Dans de nombreux cas, il peut être souhaitable de migrer les applications qui utilisent les classes de la base de données ODBC de MFC vers les classes de bases de données DAO de MFC. Cette note technique détaillera la plupart des différences entre les classes ODBC et DAO de MFC. Avec les différences à l'esprit, il ne doit pas être très difficile de migrer des applications depuis les classes ODBC vers les classes de MFC si vous le souhaitez.

## <a name="why-migrate-from-odbc-to-dao"></a>Pourquoi migrer à partir d’ODBC vers DAO

Il y a plusieurs raisons pour lesquelles vous pouvez migrer des applications depuis les classes de base de données ODBC vers les classes de base de données DAO, mais la décision n'est pas nécessairement simple ou évidente. Une chose à prendre en compte est le fait que le moteur de base de données Microsoft Jet utilisé par DAO peut indiquer une source de données ODBC pour laquelle vous avez un pilote ODBC. Il peut être plus efficace d'utiliser les classes de base de données ODBC ou d'appeler vous-même ODBC directement, mais le moteur de base de données Microsoft Jet peut lire des données ODBC.

Il existe certains cas simples qui facilitent la prise de décision ODBC/DAO. Par exemple, lorsque vous avez besoin d'accéder uniquement aux données dans un format que le moteur Microsoft Jet peut lire directement (formats Access, Excel, etc.), il devient évident de choisir l'utilisation des classes de base de données DAO.

Des cas complexes se présentent si vos données sont disponibles sur un serveur ou plusieurs serveurs. Dans ce cas, la décision d'utiliser les classes de base de données ODBC ou les classes de base de données DAO est difficile. Si vous souhaitez effectuer des opérations telles que les jointures hétérogènes (joindre des données depuis des serveurs dans plusieurs formats comme SQL Server et Oracle), le moteur de base de données Microsoft Jet effectue la jointure pour vous plutôt que de vous forcer à effectuer le travail nécessaire si vous utilisiez les classes de base de données ODBC ou si vous appeliez ODBC directement. Si vous utilisez un pilote ODBC qui prend en charge les curseurs de pilote, le meilleur choix pourrait bien être les classes de base de données ODBC.

Le choix peut être compliqué, c'est pourquoi vous pouvez entrer plusieurs exemples de code pour tester les performances des différentes méthodes données en fonction de vos besoins particuliers. Cette note technique suppose que vous avez pris la décision de migrer des classes de base de données ODBC vers des classes de base de données DAO.

## <a name="similarities-between-odbc-database-classes-and-mfc-dao-database-classes"></a>Similitudes entre les classes de base de données ODBC et les classes de base de données DAO MFC

La conception d'origine des classes ODBC MFC est basée sur le modèle d'objet DAO qui a été utilisé dans Microsoft Access et Microsoft Visual Basic. Cela signifie qu’il existe de nombreuses fonctionnalités communes aux classes ODBC et DAO MFC, qui ne seront pas toutes répertoriées dans cette section. En général, les modèles de programmation sont les mêmes.

Pour mettre en évidence les similitudes :

- Les classes ODBC et DAO disposent d'objets de base de données qui gèrent l'utilisation du système de gestion de base de données sous-jacent (SGBD).

- Les deux classes ont des objets de jeux d'enregistrements qui représentent un ensemble de résultats issus de ce système SGBD.

- Les objets de la base de données DAO et les objets des jeux d'enregistrements sont des membres quasiment identiques aux classes ODBC.

- Dans les deux jeux de classes, le code permettant d'extraire les données est identique sauf pour certaines modifications d'objet et de nom de membre. Les modifications sont nécessaires, mais généralement le processus est un changement de nom simple lorsque vous passez des classes ODBC aux classes DAO.

Par exemple, dans les deux modèles, la procédure pour récupérer des données consiste à créer et ouvrir un objet de base de données, à créer et ouvrir un objet de jeu d'enregistrements et à naviguer (se déplacer) entre les données en effectuant certaines opérations.

## <a name="differences-between-odbc-and-dao-mfc-classes"></a>Différences entre les classes ODBC et DAO de MFC

Les classes DAO incluent plus d'objets et un ensemble plus riche de méthodes, mais cette section détaillera uniquement les différences dans les classes et les fonctionnalités similaires.

Les différences les plus évidentes entre les classes sont probablement les changements de nom pour les classes semblables et les fonctions globales. La liste suivante présente les changements de nom des objets, des méthodes et des fonctions globales associés aux classes de base de données :

|Classe ou fonction|Équivalence dans les classes DAO MFC|
|-----------------------|-----------------------------------|
|`CDatabase`|`CDaoDatabase`|
|`CDatabase::ExecuteSQL`|`CDaoDatabase::Execute`|
|`CRecordset`|`CDaoRecordset`|
|`CRecordset::GetDefaultConnect`|`CDaoRecordset::GetDefaultDBName`|
|`CFieldExchange`|`CDaoFieldExchange`|
|`RFX_Bool`|`DFX_Bool`|
|`RFX_Byte`|`DFX_Byte`|
|`RFX_Int`|`DFX_Short`|
|`RFX_Long`|`DFX_Long`|
||`DFX_Currency`|
|`RFX_Single`|`DFX_Single`|
|`RFX_Double`|`DFX_Double`|
|`RFX_Date`<sup>1</sup>|`DFX_Date` (`COleDateTime`-base)|
|`RFX_Text`|`DFX_Text`|
|`RFX_Binary`|`DFX_Binary`|
|`RFX_LongBinary`|`DFX_LongBinary`|

<sup>1</sup> le `RFX_Date` fonction repose sur `CTime` et `TIMESTAMP_STRUCT`.

Les principales modifications apportées aux fonctionnalités qui peuvent affecter votre application et qui requièrent plus que de simples changements de nom sont répertoriées ci-dessous.

- Les constantes et les macros permettant de spécifier que des éléments comme le type ouvert de jeu d'enregistrements et les options ouvertes de jeu d'enregistrements ont été modifiées.

   Avec les classes ODBC, MFC avait besoin de définir ces options via des macros ou des types énumérés.

   Avec les classes DAO, DAO fournit la définition de ces options dans un fichier d'en-tête (DBDAOINT.H). Ce type d'ensemble d'enregistrements est un membre énuméré de `CRecordset`, mais avec DAO il s'agit en fait d'une constante. Par exemple, vous utiliseriez **instantané** lorsque vous spécifiez le type de `CRecordset` dans ODBC, mais **DB_OPEN_SNAPSHOT** lorsque vous spécifiez le type de `CDaoRecordset`.

- Le type de jeu d’enregistrements par défaut `CRecordset` est **instantané** tandis que le type de jeu d’enregistrements par défaut pour `CDaoRecordset` est **dynaset** (voir la Remarque ci-dessous pour un problème supplémentaire sur les instantanés de la classe ODBC).

- La classe ODBC `CRecordset` comporte une option permettant de créer un type de jeu d'enregistrements basé sur le transfert uniquement. Dans la classe `CDaoRecordset`, le transfert uniquement n'est pas un type de jeu d'enregistrements, mais plutôt une propriété (ou option) de certains types de jeux d'enregistrements.

- Un jeu d'enregistrements basé sur l'ajout uniquement lors de l'ouverture d'un objet `CRecordset` signifiait que les données du jeu d'enregistrements pouvaient être lues et ajoutées. Avec l'objet `CDaoRecordset`, l'option d'ajout uniquement signifie littéralement que les données du jeu d'enregistrements peuvent être ajoutées (et non lues).

- Les fonctions membres de la transaction des classes ODBC sont membres de `CDatabase` et agissent au niveau de la base de données. Dans les classes DAO, les fonctions membres de transaction sont membres d’une classe de niveau supérieur (`CDaoWorkspace`) et peuvent avoir un impact sur plusieurs objets `CDaoDatabase` qui partagent le même espace de travail (espace de transaction).

- La classe d'exception a été modifiée. `CDBExceptions` sont levées dans les classes ODBC et `CDaoExceptions` dans les classes DAO.

- `RFX_Date` utilise `CTime` et `TIMESTAMP_STRUCT` objets alors que `DFX_Date` utilise `COleDateTime`. Le `COleDateTime` est presque identique à `CTime`, mais est basé sur un OLE de 8 octets **DATE** au lieu de 4 octets **time_t** afin de pouvoir contenir une plage beaucoup plus volumineuse de données.

   > [!NOTE]
   > Les instantanés (`CDaoRecordset`) DAO sont en lecture seule alors que les instantanés (`CRecordset`) ODBC peuvent être modifiés selon le pilote et l'utilisation de la bibliothèque de curseurs ODBC. Si vous utilisez la bibliothèque de curseurs, les instantanés `CRecordset` sont modifiables. Si vous utilisez des pilotes Microsoft issus de Desktop Driver Pack 3.0 sans bibliothèque de curseurs ODBC, les instantanés `CRecordset` sont en lecture seule. Si vous utilisez un autre pilote, consultez la documentation du pilote pour voir si des captures instantanées (`STATIC_CURSORS`) sont en lecture seule.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
