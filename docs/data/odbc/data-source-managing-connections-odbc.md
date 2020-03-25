---
title: 'Source de données : gestion des connexions (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], multiuser environments
- generalizing connection strings
- ODBC [C++], disconnecting from data sources
- connection strings [C++], generalizing
- database connections [C++], creating
- GetDefaultConnect method
- connections [C++], data source
- ODBC connections [C++], configuring
- disconnecting from data sources
- databases [C++], connecting to
- ODBC connections [C++], disconnecting
- data sources [C++], connecting to
- ODBC connections [C++], connecting to data source
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: c0adbcdd-c000-40c6-b199-09ffdc7b6ef2
ms.openlocfilehash: 6186199ea51c1fc966783ed3c0a73496c6a307ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213291"
---
# <a name="data-source-managing-connections-odbc"></a>Source de données : gestion des connexions (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique :

- [Comment configurer une source de données](#_core_configuring_a_data_source).

- [Impact d’un environnement multi-utilisateur sur une source de données et ses recordsets](#_core_working_in_a_multiuser_environment).

- [Raisons pour lesquelles vous généralisez une chaîne de connexion à une source de données](#_core_generalizing_the_connection_string).

- [Comment se connecter à une source de données](#_core_connecting_to_a_specific_data_source).

- [Comment se déconnecter d’une source de données](#_core_disconnecting_from_a_data_source).

- [Comment réutiliser un objet CDatabase](#_core_reusing_a_cdatabase_object).

La connexion à une source de données consiste à établir des communications avec un SGBD pour accéder aux données. Lorsque vous vous connectez à une source de données à partir d’une application via un pilote ODBC, le pilote établit la connexion à votre place, localement ou sur un réseau.

Vous pouvez vous connecter à n’importe quelle source de données pour laquelle vous disposez d’un pilote ODBC. Les utilisateurs de votre application doivent également avoir le même pilote ODBC pour leur source de données. Pour plus d’informations sur la redistribution des pilotes ODBC, consultez [redistribution des composants ODBC à vos clients](../../data/odbc/redistributing-odbc-components-to-your-customers.md).

##  <a name="configuring-a-data-source"></a><a name="_core_configuring_a_data_source"></a>Configuration d’une source de données

L’administrateur ODBC est utilisé pour configurer vos sources de données. Vous pouvez également utiliser l’administrateur ODBC après l’installation pour ajouter ou supprimer des sources de données. Lorsque vous créez des applications, vous pouvez diriger vos utilisateurs vers l’administrateur ODBC pour leur permettre d’ajouter des sources de données, ou vous pouvez créer cette fonctionnalité dans votre application en effectuant des appels d’installation ODBC directs. Pour plus d’informations, consultez [ODBC Administrator](../../data/odbc/odbc-administrator.md).

Vous pouvez utiliser un fichier Excel comme source de données, et vous devez configurer le fichier pour qu’il soit inscrit et s’affiche dans la boîte de dialogue **Sélectionner la source de données** .

#### <a name="to-use-an-excel-file-as-a-data-source"></a>Pour utiliser un fichier Excel comme source de données

1. Configurez le fichier avec l’administrateur de la source de données ODBC.

1. Sous l’onglet **DSN fichier** , cliquez sur **Ajouter**.

1. Dans la boîte de dialogue **créer une nouvelle source de données** , sélectionnez un pilote Excel, puis cliquez sur **suivant**.

1. Cliquez sur **Parcourir**, puis sélectionnez le nom du fichier à utiliser comme source de date.

> [!NOTE]
>  Vous devrez peut-être sélectionner **tous les fichiers** dans le menu déroulant pour afficher les fichiers. xls.

1. Cliquez sur **Suivant**, puis sur **Terminer**.

1. Dans la boîte de dialogue **installation de Microsoft Excel ODBC** , sélectionnez la version et le classeur de la base de données.

##  <a name="working-in-a-multiuser-environment"></a><a name="_core_working_in_a_multiuser_environment"></a>Utilisation d’un environnement multi-utilisateur

Si plusieurs utilisateurs sont connectés à une source de données, ils peuvent modifier les données lors de leur manipulation dans vos recordsets. De même, vos modifications peuvent affecter les recordsets des autres utilisateurs. Pour plus d’informations, consultez [Recordset : mode de mise à jour des enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) et [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="generalizing-the-connection-string"></a><a name="_core_generalizing_the_connection_string"></a>Généralisation de la chaîne de connexion

Les assistants utilisent une chaîne de connexion par défaut pour établir une connexion à une source de données. Vous utilisez cette connexion pour afficher les tables et les colonnes pendant que vous développez votre application. Toutefois, cette chaîne de connexion par défaut peut ne pas convenir aux connexions de vos utilisateurs à la source de données par le biais de votre application. Par exemple, la source de données et le chemin d’accès à son emplacement peuvent être différents de ceux utilisés lors du développement de votre application. Dans ce cas, vous devez réimplémenter la fonction membre [CRecordset :: GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) de manière plus générique et ignorer l’implémentation de l’Assistant. Par exemple, utilisez l’une des approches suivantes :

- Inscrire et gérer les chaînes de connexion à l’aide de l’administrateur ODBC.

- Modifiez la chaîne de connexion et supprimez le nom de la source de données. L’infrastructure fournit ODBC comme source de données ; au moment de l’exécution, ODBC affiche une boîte de dialogue qui vous demande le nom de la source de données et les autres informations de connexion requises.

- Fournissez uniquement le nom de la source de données. ODBC vous demande l’ID d’utilisateur et le mot de passe, si nécessaire. Par exemple, avant la généralisation, la chaîne de connexion se présente comme suit :

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   Cette chaîne de connexion spécifie une connexion approuvée, qui utilise la sécurité intégrée de Windows NT. Vous devez éviter de coder en dur un mot de passe ou de spécifier un mot de passe vide, car cela crée une faille de sécurité majeure. Au lieu de cela, vous pouvez attribuer à `GetDefaultConnect` une nouvelle chaîne de connexion pour qu’elle interroge un ID d’utilisateur et un mot de passe.

    ```cpp
    // User must select data source and supply user ID and password:
        return "ODBC;";
    // User ID and password required:
        return "ODBC;DSN=mydb;";
    // Password required (myuserid must be replaced with a valid user ID):
        return "ODBC;DSN=mydb;UID=myuserid;";
    // Hard-coded user ID and password (SECURITY WEAKNESS--AVOID):
        return "ODBC;DSN=mydb;UID=sa;PWD=777;";
    ```

##  <a name="connecting-to-a-specific-data-source"></a><a name="_core_connecting_to_a_specific_data_source"></a>Connexion à une source de données spécifique

Pour vous connecter à une source de données spécifique, votre source de données doit déjà avoir été configurée avec l' [administrateur ODBC](../../data/odbc/odbc-administrator.md).

#### <a name="to-connect-to-a-specific-data-source"></a>Pour se connecter à une source de données spécifique

1. Construisez un objet `CDatabase`.

1. Appelez sa fonction membre `OpenEx` ou `Open`.

Pour plus d’informations sur la façon de spécifier la source de données si elle est différente de celle que vous avez spécifiée à l’aide d’un Assistant, consultez [CDatabase :: OpenEx](../../mfc/reference/cdatabase-class.md#openex) ou [CDatabase :: Open](../../mfc/reference/cdatabase-class.md#open) dans la *référence MFC*.

##  <a name="disconnecting-from-a-data-source"></a><a name="_core_disconnecting_from_a_data_source"></a>Déconnexion d’une source de données

Vous devez fermer tous les jeux d’enregistrements ouverts avant d’appeler la fonction membre `Close` de `CDatabase`. Dans les jeux d’enregistrements associés à l’objet `CDatabase` que vous souhaitez fermer, les instructions `AddNew` ou `Edit` en attente sont annulées et toutes les transactions en attente sont annulées.

#### <a name="to-disconnect-from-a-data-source"></a>Pour se déconnecter d’une source de données

1. Appelez la fonction membre [Close](../../mfc/reference/cdatabase-class.md#close) de l’objet `CDatabase`.

1. Détruisez l’objet, sauf si vous souhaitez le réutiliser.

##  <a name="reusing-a-cdatabase-object"></a><a name="_core_reusing_a_cdatabase_object"></a>Réutilisation d’un objet CDatabase

Vous pouvez réutiliser un objet `CDatabase` après l’avoir déconnectée, que vous l’utilisiez pour vous reconnecter à la même source de données ou que vous vous connectiez à une source de données différente.

#### <a name="to-reuse-a-cdatabase-object"></a>Pour réutiliser un objet CDatabase

1. Fermez la connexion d’origine de l’objet.

1. Au lieu de détruire l’objet, appelez à nouveau sa fonction membre `OpenEx` ou `Open`.

## <a name="see-also"></a>Voir aussi

[Source de données (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Source de données : détermination du schéma de la source de données (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset, classe](../../mfc/reference/crecordset-class.md)
