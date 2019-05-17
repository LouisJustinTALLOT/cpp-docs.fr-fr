---
title: Création d'un consommateur sans utiliser l'Assistant
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
ms.openlocfilehash: 421723ed561e8ed986a64024c4c5d29c9fba6110
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525115"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>Création d'un consommateur sans utiliser l'Assistant

L’exemple suivant suppose que vous ajoutez la prise en charge du consommateur OLE DB à un projet ATL existant. Si vous souhaitez ajouter la prise en charge du consommateur OLE DB à une application MFC, vous devez exécuter l’**Assistant Application MFC**, qui crée toute la prise en charge nécessaire et appelle les routines MFC nécessaires pour exécuter l’application.

Pour ajouter la prise en charge du consommateur OLE DB sans utiliser l’**Assistant Consommateur OLE DB ATL**:

- Dans votre fichier pch.h, ajoutez les instructions `#include` suivantes :

    ```cpp
    #include <atlbase.h>
    #include <atldbcli.h>
    #include <atldbsch.h> // if you are using schema templates
    ```

Par programmation, un consommateur exécute généralement la séquence d’opérations suivante :

1. Créez une classe d’enregistrement utilisateur qui lie les colonnes aux variables locales. Dans cet exemple, `CMyTableNameAccessor` est la classe d’enregistrement utilisateur (consultez [Enregistrements utilisateur](../../data/oledb/user-records.md)). Cette classe contient le mappage de colonnes et le mappage de paramètre. Déclarez un membre de données dans la classe d’enregistrement utilisateur pour chaque champ que vous spécifiez dans votre mappage de colonne. Pour chacun de ces membres de données, déclarez également un membre de données d’état et un membre de données de longueur. Pour plus d’informations, consultez [Membre de données d’état des champs dans les accesseurs générés par l’Assistant](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

    > [!NOTE]
    > Si vous écrivez votre propre consommateur, les variables de données doivent précéder les variables d’état et de longueur.

- Instanciez une source de données et une session. Décidez du type d’accesseur et d’ensemble de lignes à utiliser, puis instanciez un ensemble de lignes à l’aide de [CCommand](../../data/oledb/ccommand-class.md) ou [CTable](../../data/oledb/ctable-class.md) :

    ```cpp
    CDataSource ds;
    CSession ss;
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>
    ```

- Appelez `CoInitialize` pour initialiser COM. Il est appelé dans le code principal. Par exemple :

    ```cpp
    HRESULT hr = CoInitialize(NULL);
    ```

- Appelez [CDataSource::Open](../../data/oledb/cdatasource-open.md) ou une de ses variantes.

- Ouvrez une connexion à la source de données, ouvrez la session puis ouvrez et initialisez l’ensemble de lignes (s’il s’agit d’une commande, exécutez-la aussi) :

    ```cpp
    hr = ds.Open();
    hr = ss.Open(ds);
    hr = rs.Open();            // (Open also executes the command)
    ```

- Si vous le souhaitez, définissez des propriétés l’aide de `CDBPropSet::AddProperty` et passez-les en tant que paramètre à `rs.Open`. Pour obtenir un exemple de cette procédure, consultez `GetRowsetProperties` dans [Méthodes de consommateur générées par l’Assistant](../../data/oledb/consumer-wizard-generated-methods.md).

- Vous pouvez maintenant utiliser l’ensemble de lignes pour récupérer/manipuler les données.

- Quand votre application est terminée, fermez la connexion, la session et l’ensemble de lignes :

    ```cpp
    rs.Close();
    ss.Close();
    ds.Close();
    ```

   Si vous utilisez une commande, il est conseillé d’appeler `ReleaseCommand` après `Close`. L’exemple de code dans [CCommand::Close](../../data/oledb/ccommand-close.md) montre comment appeler `Close` et `ReleaseCommand`.

- Appelez `CoUnInitialize` pour annuler l’initialisation de COM. Il est appelé dans le code principal.

    ```cpp
    CoUninitialize();
    ```

## <a name="see-also"></a>Voir aussi

[Création d’un consommateur OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)