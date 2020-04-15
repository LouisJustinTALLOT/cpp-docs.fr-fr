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
ms.openlocfilehash: 107a5e20b70f67be74b6e6f861bd539446e9d4ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374530"
---
# <a name="data-source-managing-connections-odbc"></a>Source de données : gestion des connexions (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique répond aux questions suivantes :

- [Comment configurer une source de données](#_core_configuring_a_data_source).

- [Comment un environnement multi-utilisateurs affecte une source de données et ses enregistrements](#_core_working_in_a_multiuser_environment).

- [Pourquoi vous généralisez une chaîne de connexion à une source de données](#_core_generalizing_the_connection_string).

- [Comment se connecter à une source](#_core_connecting_to_a_specific_data_source)de données .

- [Comment se déconnecter d’une source de données](#_core_disconnecting_from_a_data_source).

- [Comment réutiliser un objet CDatabase](#_core_reusing_a_cdatabase_object).

Se connecter à une source de données signifie établir des communications avec un DBMS pour accéder aux données. Lorsque vous vous connectez à une source de données à partir d’une application via un pilote ODBC, le pilote vous connecte, soit localement, soit sur un réseau.

Vous pouvez vous connecter à n’importe quelle source de données pour laquelle vous avez un pilote ODBC. Les utilisateurs de votre application doivent également avoir le même pilote ODBC pour leur source de données. Pour plus d’informations sur la redistribution des pilotes ODBC, voir [Redistribuer les composants ODBC à vos clients](../../data/odbc/redistributing-odbc-components-to-your-customers.md).

## <a name="configuring-a-data-source"></a><a name="_core_configuring_a_data_source"></a>Configurer une source de données

L’administrateur d’ODBC est utilisé pour configurer vos sources de données. Vous pouvez également utiliser oDBC Administrator après installation pour ajouter ou supprimer des sources de données. Lorsque vous créez des applications, vous pouvez soit diriger vos utilisateurs vers l’administrateur ODBC pour les laisser ajouter des sources de données ou vous pouvez intégrer cette fonctionnalité dans votre application en effectuant des appels d’installation ODBC directs. Pour plus d’informations, voir [ODBC Administrateur](../../data/odbc/odbc-administrator.md).

Vous pouvez utiliser un fichier Excel comme source de données, et vous devez configurer le fichier afin qu’il soit enregistré et s’affiche dans la boîte de dialogue **Select Data Source.**

#### <a name="to-use-an-excel-file-as-a-data-source"></a>Utiliser un fichier Excel comme source de données

1. Configurez le fichier avec l’administrateur de source de données ODBC.

1. Sur l’onglet **Fichier DSN,** cliquez sur **Ajouter**.

1. Dans la boîte de dialogue **Create New Data Source,** sélectionnez un pilote Excel, puis cliquez sur **Next**.

1. Cliquez **sur Parcourir**, et sélectionnez le nom du fichier à utiliser comme source de date.

> [!NOTE]
> Vous devrez peut-être sélectionner **tous les fichiers** dans le menu drop-down pour afficher les fichiers .xls.

1. Cliquez sur **Suivant**, puis sur **Terminer**.

1. Dans la boîte de dialogue **ODBC Microsoft Excel Setup,** sélectionnez la version de base de données et le carnet de travail.

## <a name="working-in-a-multiuser-environment"></a><a name="_core_working_in_a_multiuser_environment"></a>Travailler dans un environnement multi-travailleurs

Si plusieurs utilisateurs sont connectés à une source de données, ils peuvent modifier les données pendant que vous les manipulez dans vos enregistrements. De même, vos modifications peuvent affecter les enregistrements d’autres utilisateurs. Pour plus d’informations, voir [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) et [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="generalizing-the-connection-string"></a><a name="_core_generalizing_the_connection_string"></a>Généraliser la chaîne de connexion

Les assistants utilisent une chaîne de connexion par défaut pour établir une connexion à une source de données. Vous utilisez cette connexion pour afficher des tables et des colonnes pendant que vous développez votre application. Toutefois, cette chaîne de connexion par défaut peut ne pas convenir aux connexions de vos utilisateurs à la source de données via votre application. Par exemple, leur source de données et le chemin vers son emplacement peuvent être différents de celui utilisé dans le développement de votre application. Dans ce cas, vous devez réimplanter le [CRecordset::GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) fonction membre d’une manière plus générique et jeter l’implémentation assistant. Par exemple, utilisez l’une des approches suivantes :

- Inscrivez-vous et gérez les chaînes de connexion à l’aide de l’administrateur ODBC.

- Modifier la chaîne de connexion et supprimer le nom de source de données. Le cadre fournit oDBC comme source de données; au moment de l’exécution, ODBC affiche une boîte de dialogue demandant le nom de source de données et toute autre information de connexion requise.

- Fournir le nom de source de données seulement. ODBC demande l’identifiant et le mot de passe de l’utilisateur, si nécessaire. Par exemple, avant de généraliser, la chaîne de connexion ressemble à ceci :

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   Cette chaîne de connexion spécifie une connexion de confiance, qui utilise la sécurité intégrée de Windows NT. Vous devez éviter de coder un mot de passe ou de spécifier un mot de passe vierge, car cela crée une faiblesse de sécurité majeure. Au lieu de `GetDefaultConnect` cela, vous pouvez donner une nouvelle chaîne de connexion afin qu’il interroge pour un identifiant d’utilisateur et mot de passe.

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

## <a name="connecting-to-a-specific-data-source"></a><a name="_core_connecting_to_a_specific_data_source"></a>Se connecter à une source de données spécifique

Pour vous connecter à une source de données spécifique, votre source de données doit déjà avoir été configurée avec [oDBC Administrator](../../data/odbc/odbc-administrator.md).

#### <a name="to-connect-to-a-specific-data-source"></a>Pour vous connecter à une source de données spécifique

1. Construire `CDatabase` un objet.

1. Appelez `OpenEx` sa `Open` fonction ou sa fonction de membre.

Pour plus d’informations sur la façon de spécifier la source de données si c’est autre chose que celui que vous avez spécifié avec un assistant, voir [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) ou [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) in the *MFC Reference*.

## <a name="disconnecting-from-a-data-source"></a><a name="_core_disconnecting_from_a_data_source"></a>Déconnecter d’une source de données

Vous devez fermer tous les `Close` enregistrements ouverts `CDatabase`avant d’appeler la fonction membre de . Dans les enregistrements `CDatabase` associés à l’objet que `AddNew` `Edit` vous souhaitez fermer, toute déclaration en attente ou déclarations est annulée et toutes les transactions en attente sont annulées.

#### <a name="to-disconnect-from-a-data-source"></a>Pour se déconnecter d’une source de données

1. Appelez `CDatabase` la fonction de membre [Close](../../mfc/reference/cdatabase-class.md#close) de l’objet.

1. Détruisez l’objet à moins que vous ne vouliez le réutiliser.

## <a name="reusing-a-cdatabase-object"></a><a name="_core_reusing_a_cdatabase_object"></a>Réutiliser un objet CDatabase

Vous pouvez réutiliser un `CDatabase` objet après s’en être déconnecté, que vous l’utilisiez pour vous reconnecter à la même source de données ou pour vous connecter à une source de données différente.

#### <a name="to-reuse-a-cdatabase-object"></a>Pour réutiliser un objet CDatabase

1. Fermez la connexion d’origine de l’objet.

1. Au lieu de détruire l’objet, appelez à nouveau sa `OpenEx` fonction ou `Open` sa fonction de membre.

## <a name="see-also"></a>Voir aussi

[Source de données (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Source de données : détermination du schéma de la source de données (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)
