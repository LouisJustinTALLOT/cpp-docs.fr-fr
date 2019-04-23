---
title: Création d'un consommateur sans utiliser l'Assistant
ms.date: 10/12/2018
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
ms.openlocfilehash: 029fe6866df81d366cc3bc15096f638791faa413
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030418"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>Création d'un consommateur sans utiliser l'Assistant

L’exemple suivant suppose que vous ajoutez prise en charge du consommateur OLE DB à un projet ATL existant. Si vous souhaitez ajouter la prise en charge du consommateur OLE DB à une application MFC, vous devez exécuter le **Assistant Application MFC**, qui crée la prise en charge nécessaire et appelle les routines MFC nécessaires pour exécuter l’application.

Pour ajouter la prise en charge du consommateur OLE DB sans utiliser le **Assistant Consommateur OLE DB ATL**:

- Dans votre fichier pch.h, ajoutez le code suivant `#include` instructions :

    ```cpp
    #include <atlbase.h>
    #include <atldbcli.h>
    #include <atldbsch.h> // if you are using schema templates
    ```

Par programmation, un consommateur exécute généralement la séquence d’opérations suivante :

1. Créez une classe d’enregistrement utilisateur qui lie les colonnes aux variables locales. Dans cet exemple, `CMyTableNameAccessor` est la classe d’enregistrement utilisateur (consultez [enregistrements utilisateur](../../data/oledb/user-records.md)). Cette classe contient le mappage de colonnes et le mappage de paramètre. Déclarez un membre de données dans la classe d’enregistrement utilisateur pour chaque champ que vous spécifiez dans le mappage de colonne ; pour chacun de ces membres de données, également déclarer un membre de données d’état et un membre de données de longueur. Pour plus d’informations, consultez [données membres de l’état des champs dans les accesseurs](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

    > [!NOTE]
    > Si vous écrivez votre propre consommateur, les variables de données doivent précéder les variables d’état et de longueur.

- Instancier une source de données et d’une session. Décider quel type d’accesseur et ensemble de lignes à utiliser, puis instanciation d’un ensemble de lignes à l’aide [CCommand](../../data/oledb/ccommand-class.md) ou [CTable](../../data/oledb/ctable-class.md):

    ```cpp
    CDataSource ds;
    CSession ss;
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>
    ```

- Appelez `CoInitialize` initialisation de COM. Il s’agit dans le code principal. Exemple :

    ```cpp
    HRESULT hr = CoInitialize(NULL);
    ```

- Appelez [CDataSource::Open](../../data/oledb/cdatasource-open.md) ou une de ses variantes.

- Ouvrez une connexion à la source de données, ouvrez la session et ouvrir et initialiser l’ensemble de lignes (et si une commande, aussi l’exécuter) :

    ```cpp
    hr = ds.Open();
    hr = ss.Open(ds);
    hr = rs.Open();            // (Open also executes the command)
    ```

- Si vous le souhaitez, définition des propriétés de jeu de lignes à l’aide de `CDBPropSet::AddProperty` et les passer en tant que paramètre à `rs.Open`. Pour obtenir un exemple de cette procédure, consultez `GetRowsetProperties` dans [Consumer Wizard-Generated méthodes](../../data/oledb/consumer-wizard-generated-methods.md).

- Vous pouvez maintenant utiliser l’ensemble de lignes pour récupérer/manipuler les données.

- Quand votre application est terminée, fermez la connexion, une session et un ensemble de lignes :

    ```cpp
    rs.Close();
    ss.Close();
    ds.Close();
    ```

   Si vous utilisez une commande, vous souhaiterez appeler `ReleaseCommand` après `Close`. L’exemple de code dans [CCommand::Close](../../data/oledb/ccommand-close.md) montre comment appeler `Close` et `ReleaseCommand`.

- Appeler `CoUnInitialize` pour annuler l’initialisation de COM. Il s’agit dans le code principal.

    ```cpp
    CoUninitialize();
    ```

## <a name="see-also"></a>Voir aussi

[Création d’un consommateur OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)