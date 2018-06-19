---
title: Création d’un consommateur sans utiliser d’Assistant | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c9f6bbc1ba45ec0b510dac015688fd29801c8449
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097690"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>Création d'un consommateur sans utiliser l'Assistant
L’exemple suivant suppose que vous ajoutez la prise en charge du consommateur OLE DB à un projet ATL existant. Si vous souhaitez ajouter la prise en charge du consommateur OLE DB à une application MFC, vous devez exécuter l’Assistant Application MFC, qui crée la prise en charge nécessaire et appelle les routines MFC nécessaires pour l’exécution de l’application.  
  
 Pour ajouter la prise en charge du consommateur OLE DB sans utiliser l’Assistant Consommateur OLE DB ATL :  
  
-   Dans votre fichier Stdafx.h, ajoutez le code suivant `#include` instructions :  
  
    ```  
    #include <atlbase.h>  
    #include <atldbcli.h>  
    #include <atldbsch.h> // if you are using schema templates  
    ```  
  
 Par programme, un consommateur exécute généralement la séquence d’opérations suivante :  
  
-   Créez une classe d’enregistrement utilisateur qui lie les colonnes aux variables locales. Dans cet exemple, `CMyTableNameAccessor` est la classe d’enregistrement utilisateur (consultez [enregistrements utilisateur](../../data/oledb/user-records.md)). Cette classe contient le mappage de colonnes et le mappage de paramètre. Déclarez un membre de données dans la classe d’enregistrement utilisateur pour chaque champ que vous spécifiez dans le mappage de colonnes ; pour chacun de ces membres de données, également déclarer un membre de données d’état et un membre de données de longueur. Pour plus d’informations, consultez [données membres de l’état des champs dans les accesseurs](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
    > [!NOTE]
    >  Si vous écrivez votre propre consommateur, les variables de données doivent précéder les variables d’état et de longueur.  
  
-   Instancier une source de données et d’une session. Détermination du type d’accesseur et ensemble de lignes à utiliser, puis instanciation d’un ensemble de lignes à l’aide de [CCommand](../../data/oledb/ccommand-class.md) ou [CTable](../../data/oledb/ctable-class.md):  
  
    ```  
    CDataSource ds;  
    CSession ss;  
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>  
    ```  
  
-   Appelez **CoInitialize** initialiser COM. Cela est généralement appelé dans le code principal. Par exemple :  
  
    ```  
    HRESULT hr = CoInitialize(NULL);  
    ```  
  
-   Appelez [CDataSource::Open](../../data/oledb/cdatasource-open.md) ou l’une de ses variantes.  
  
-   Ouvrir une connexion à la source de données, ouvrez la session et ouvrir et initialiser l’ensemble de lignes (et si une commande, l’exécuter également) :  
  
    ```  
    hr = ds.Open();  
    hr = ss.Open(ds);  
    hr = rs.Open();            // (Open also executes the command)  
    ```  
  
-   Si vous le souhaitez, définition des propriétés de jeu de lignes à l’aide de `CDBPropSet::AddProperty` et les passer en tant que paramètre à `rs.Open`. Pour obtenir un exemple de cette procédure, consultez GetRowsetProperties dans [Consumer Wizard-Generated méthodes](../../data/oledb/consumer-wizard-generated-methods.md).  
  
-   Vous pouvez maintenant utiliser l’ensemble de lignes pour extraire/manipuler les données.  
  
-   Lorsque votre application est terminée, fermez la connexion, une session et un ensemble de lignes :  
  
    ```  
    rs.Close();  
    ss.Close();  
    ds.Close();  
    ```  
  
     Si vous utilisez une commande, vous pouvez souhaiter appeler `ReleaseCommand` après **fermer**. L’exemple de code [CCommand::Close](../../data/oledb/ccommand-close.md) montre comment appeler **fermer** et `ReleaseCommand`.  
  
-   Appelez **CoUnInitialize** annuler l’initialisation de COM. Cela est généralement appelé dans le code principal.  
  
    ```  
    CoUninitialize();  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un consommateur OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)