---
title: 'Source de données : Gestion des connexions (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 100c06773a8f0ffa79631339384bd4ec42fa4b52
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091827"
---
# <a name="data-source-managing-connections-odbc"></a>Source de données : gestion des connexions (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Cette rubrique explique :  
  
-   [Comment configurer une source de données](#_core_configuring_a_data_source).  
  
-   [Comment un environnement multi-utilisateur affecte une source de données et ses jeux d’enregistrements](#_core_working_in_a_multiuser_environment).  
  
-   [Pourquoi généraliser une chaîne de connexion à une source de données](#_core_generalizing_the_connection_string).  
  
-   [Comment se connecter à une source de données](#_core_connecting_to_a_specific_data_source).  
  
-   [Comment se déconnecter d’une source de données](#_core_disconnecting_from_a_data_source).  
  
-   [Comment réutiliser un objet CDatabase](#_core_reusing_a_cdatabase_object).  
  
 Connexion à une source de données signifie l’établissement de communications avec un système SGBD pour accéder aux données. Lorsque vous vous connectez à une source de données à partir d’une application via un pilote ODBC, le pilote établit la connexion pour vous, localement ou sur un réseau.  
  
 Vous pouvez vous connecter à n’importe quelle source de données pour lequel vous avez un pilote ODBC. Les utilisateurs de votre application doivent également avoir le même pilote ODBC pour leur source de données. Pour plus d’informations sur la redistribution de pilotes ODBC, consultez [redistribution des composants ODBC à vos clients](../../data/odbc/redistributing-odbc-components-to-your-customers.md).  
  
##  <a name="_core_configuring_a_data_source"></a> Configuration d’une Source de données  
 Administrateur ODBC est utilisé pour configurer vos sources de données. Vous pouvez également utiliser l’administrateur ODBC après l’installation pour ajouter ou supprimer des sources de données. Lorsque vous créez des applications, vous pouvez diriger vos utilisateurs à l’administrateur ODBC pour leur permettre d’ajouter des sources de données, ou vous pouvez intégrer cette fonctionnalité dans votre application en effectuant des appels d’installation ODBC directs. Pour plus d’informations, consultez [administrateur ODBC](../../data/odbc/odbc-administrator.md).  
  
 Vous pouvez utiliser un fichier Excel comme source de données, et vous devez configurer le fichier afin qu’il est enregistré et s’affiche dans le **sélectionner une Source de données** boîte de dialogue.  
  
#### <a name="to-use-an-excel-file-as-a-data-source"></a>Pour utiliser un fichier Excel comme source de données  
  
1.  Configurez le fichier avec l’administrateur de Source de données ODBC.  
  
2.  Sur le **DSN de fichier** , cliquez sur **ajouter**.  
  
3.  Dans le **créer une nouvelle Source de données** boîte de dialogue, sélectionnez un pilote Excel, puis cliquez sur **suivant**.  
  
4.  Cliquez sur **Parcourir**, puis sélectionnez le nom du fichier à utiliser comme source.  
  
> [!NOTE]
>  Vous devrez peut-être sélectionner **tous les fichiers** dans le menu déroulant pour afficher les fichiers .xls.  
  
1.  Cliquez sur **Suivant**, puis sur **Terminer**.  
  
2.  Dans le **installation ODBC pour Microsoft Excel** boîte de dialogue, sélectionnez la base de données de Version et le classeur.  
  
##  <a name="_core_working_in_a_multiuser_environment"></a> Vous travaillez dans un environnement multi-utilisateur  
 Si plusieurs utilisateurs sont connectés à une source de données, ils peuvent modifier les données pendant que vous manipulez dans vos jeux d’enregistrements. De même, les modifications peuvent affecter les recordsets des autres utilisateurs. Pour plus d’informations, consultez [Recordset : modification des enregistrements de jeux d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) et [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="_core_generalizing_the_connection_string"></a> La généralisation de la chaîne de connexion  
 Les Assistants utilisent une chaîne de connexion par défaut pour établir une connexion à une source de données. Cette connexion vous permet d’afficher les tables et colonnes lorsque vous développez votre application. Toutefois, cette chaîne de connexion par défaut ne peut pas être appropriée pour les connexions des utilisateurs à la source de données via votre application. Par exemple, leur source de données et le chemin d’accès à son emplacement peuvent être différents de celui utilisé dans le développement de votre application. Dans ce cas, vous devez réimplémenter les [CRecordset::GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) membre fonctionne de façon plus générique et abandonner l’implémentation de l’Assistant. Par exemple, utilisez une des approches suivantes :  
  
-   Enregistrez et gérez les chaînes de connexion à l’aide de l’administrateur ODBC.  
  
-   Modifier la chaîne de connexion et supprimez le nom de source de données. La structure fournit ODBC comme source de données ; au moment de l’exécution, ODBC affiche une boîte de dialogue demandant les informations de nom et les autres connexions requis de source de données.  
  
-   Fournissez uniquement le nom de la source de données. ODBC vous demande l’ID utilisateur et un mot de passe, si nécessaire. Par exemple, avant la généralisation, la chaîne de connexion ressemble à ceci :  
  
    ```  
    CString CApp1Set::GetDefaultConnect()  
    {  
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";  
    }  
    ```  
  
     Cette chaîne de connexion spécifie une connexion approuvée, qui utilise la sécurité intégrée de Windows NT. Vous devez éviter de coder en dur un mot de passe ou en spécifiant un mot de passe vide, car cela crée une faille de sécurité majeur. Au lieu de cela, vous pouvez donner à `GetDefaultConnect` une nouvelle chaîne de connexion afin qu’elle demande un ID d’utilisateur et un mot de passe.  
  
    ```  
    // User must select data source and supply user ID and password:  
        return "ODBC;";  
    // User ID and password required:  
        return "ODBC;DSN=mydb;";  
    // Password required (myuserid must be replaced with a valid user ID):  
        return "ODBC;DSN=mydb;UID=myuserid;";  
    // Hard-coded user ID and password (SECURITY WEAKNESS--AVOID):  
        return "ODBC;DSN=mydb;UID=sa;PWD=777;";  
    ```  
  
##  <a name="_core_connecting_to_a_specific_data_source"></a> Connexion à une Source de données spécifique  
 Pour vous connecter à une source de données spécifique, votre source de données doit déjà avoir été configurée avec [administrateur ODBC](../../data/odbc/odbc-administrator.md).  
  
#### <a name="to-connect-to-a-specific-data-source"></a>Pour vous connecter à une source de données spécifique  
  
1.  Construire un `CDatabase` objet.  
  
2.  Appeler son `OpenEx` ou **ouvrir** fonction membre.  
  
 Pour plus d’informations sur la façon de spécifier la source de données s’il s’agit d’un élément autre que celui que vous avez spécifié à l’aide d’un Assistant, consultez [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) ou [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) dans le *MFC Référence*.  
  
##  <a name="_core_disconnecting_from_a_data_source"></a> Déconnexion d’une Source de données  
 Vous devez fermer tous les recordsets ouverts avant d’appeler le **fermer** fonction membre de `CDatabase`. Dans les jeux d’enregistrements associés la `CDatabase` vous voulez fermer, tout en attente de l’objet `AddNew` ou **modifier** instructions sont et toutes les transactions en attente sont annulées.  
  
#### <a name="to-disconnect-from-a-data-source"></a>Pour se déconnecter d’une source de données  
  
1.  Appelez le `CDatabase` l’objet [fermer](../../mfc/reference/cdatabase-class.md#close) fonction membre.  
  
2.  Détruire l’objet, sauf si vous souhaitez réutiliser.  
  
##  <a name="_core_reusing_a_cdatabase_object"></a> Réutilisation d’un objet CDatabase  
 Vous pouvez réutiliser un `CDatabase` objet après la déconnexion, si vous l’utilisez pour vous reconnecter à la même source de données ou pour vous connecter à une autre source de données.  
  
#### <a name="to-reuse-a-cdatabase-object"></a>Pour réutiliser un objet CDatabase  
  
1.  Fermez la connexion d’origine de l’objet.  
  
2.  Au lieu de détruire l’objet, appelez sa `OpenEx` ou **ouvrir** fonction membre à nouveau.  
  
## <a name="see-also"></a>Voir aussi  
 [Source de données (ODBC)](../../data/odbc/data-source-odbc.md)   
 [Source de données : Détermination du schéma de la Source de données (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)   
 [CRecordset, classe](../../mfc/reference/crecordset-class.md)