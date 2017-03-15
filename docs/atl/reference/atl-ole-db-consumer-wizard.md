---
title: "L’Assistant Consommateur ATL OLE DB | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.consumer.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- connection strings [C++], OLE DB consumers
- ATL OLE DB Consumer Wizard
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 6e35ce9038a8fd8f7aeeb00139511a8f45c1257d
ms.lasthandoff: 02/24/2017

---
# <a name="atl-ole-db-consumer-wizard"></a>Assistant Consommateur OLEDB ATL
Cet Assistant définit une classe de consommateur OLE DB avec les liaisons de données nécessaire pour accéder à la source de données spécifié via le fournisseur OLE DB spécifié.  
  
> [!NOTE]
>  Cet Assistant nécessite que vous cliquez sur le **Source de données** bouton pour sélectionner une source de données avant d’entrer des noms dans le `Class` et **fichier .h** champs.  
  
## <a name="uielement-list"></a>Liste UIElement  
 **Source de données**  
 Le **Source de données** bouton vous permet de définir la source de données spécifiée à l’aide du fournisseur OLE DB spécifié. Lorsque vous cliquez sur ce bouton, le **propriétés des liaisons de données** boîte de dialogue s’affiche. Pour plus d’informations sur la création de chaînes de connexion et le **propriétés des liaisons de données** boîte de dialogue, consultez [Data Link API Overview](https://msdn.microsoft.com/library/ms718102.aspx) dans les [!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)] documentation.  
  
> [!NOTE]
>  Dans les versions précédentes, en cliquant sur MAJ le **Source de données** bouton ouverte une boîte de dialogue Ouvrir le fichier pour vous permettre de sélectionner un fichier Data Link (.udl). Cette fonctionnalité n’est plus pris en charge.  
  
 La boîte de dialogue comporte quatre onglets :  
  
- **Fournisseur** onglet  
  
- **Connexion** onglet  
  
- **Advanced** onglet  
  
- **Tous les** onglet  
  
     Les informations supplémentaires suivantes décrivent les onglets de la **propriétés des liaisons de données** boîte de dialogue.  
  
     Cliquez sur **OK** à terminer. Le **sélectionner un objet de base de données** boîte de dialogue s’affiche. Dans cette boîte de dialogue, sélectionnez la table, une vue ou une procédure stockée que le consommateur doit utiliser.  
  
 **Fournisseur**  
     Sélectionnez un fournisseur approprié pour gérer la connexion à la source de données. Le type de fournisseur est généralement déterminé par le type de base de données à laquelle vous vous connectez. Cliquez sur le `Next` bouton ou cliquez sur le **connexion** onglet.  
  
 **Connexion**  
     Le contenu de cet onglet dépend du fournisseur sélectionné. Bien qu’il existe de nombreux types de fournisseurs, cette section traite des connexions pour les deux plus courants : données SQL et ODBC. Les autres sont des variations similaires sur les champs décrits ici.  
  
     Pour les données SQL :  
  
    1. **Sélectionner ou entrer un nom de serveur :** cliquez sur le menu déroulant pour afficher tous les serveurs de données inscrites sur le réseau, puis sélectionnez une.  
  
    2. **Entrez les informations pour vous connecter au serveur :** permet d’entrer un nom d’utilisateur et le mot de passe pour ouvrir une session sur le serveur de données.  
  
    3. **Sélectionnez la base de données sur le serveur :** cliquez sur le menu déroulant pour afficher inscrits toutes les bases de données sur le serveur de données et sélectionnez un.  
  
         ou  
  
 **Joindre un fichier de base de données comme un nom de base de données :** spécifier un fichier à utiliser comme base de données, entrez le chemin d’accès explicite.  
  
        > [!NOTE]
        >  There is a security problem with the "Allow saving of password" feature of the Data Link Properties dialog box. In "Enter information to log on to the server," there are two radio buttons:  
  
 **Utilisez la sécurité intégrée de Windows NT**  
  
 **Utilisez un nom d’utilisateur spécifique et un mot de passe**  
  
         If you select **Use a specific user name and password**, you have the option of saving the password (using the check box for "Allow saving password"); however, this option is not secure. It is recommended that you select **Use Windows NT integrated security**; this option is secure because it encrypts the password.  
  
         There might be situations in which you want to select "Allow saving password." For example, if you are releasing a library with a private database solution, you should not access the database directly but instead use a middle-tier application to verify the user (through whatever authentication scheme you choose) and then limit the sort of data available to the user.  
  
         For ODBC data:  
  
         1. **Specify the source of data:** You can use a data source name or a connection string.  
  
 **Nom de source de données utilisation :** cette liste déroulante affiche les sources de données inscrites sur votre ordinateur. Vous pouvez définir des sources de données à l’aide de l’administrateur de sources de données ODBC- ou -**utiliser la chaîne de connexion :** Entrez une chaîne de connexion que vous avez déjà obtenu, ou cliquez sur le **Build** bouton ; le **sélectionner une Source de données** boîte de dialogue s’affiche. Sélectionnez une source de données fichier ou machine, cliquez sur **OK**.  
  
        > [!NOTE]
        >  You can obtain a connection string by viewing the properties of an existing connection in Server Explorer, or you can create a connection by double-clicking **Add Connection** in Server Explorer.  
  
         2. **Enter information to log on to the server:** Enter a user name and password to log on to the data server.  
  
         3. Enter the initial catalog to use.  
  
         4. Click **Test Connection**; if the test succeeds, click **OK**. If not, check your logon information, try another database, or try another data server.  
  
 **Avancé**  
 **Paramètres réseau :** spécifier le **au niveau d’emprunt d’identité** (le niveau d’emprunt d’identité que le serveur est autorisé à utiliser lors de l’emprunt d’identité du client ; correspond directement aux niveaux d’emprunt d’identité RPC) et **niveau de Protection** (le niveau de protection des données envoyées entre le client et le serveur ; correspond directement à des niveaux de protection RPC).  
  
 **Autres :** dans **délai de connexion**, spécifiez le nombre de secondes d’inactivité autorisée avant qu’un délai d’attente se produit. Dans **les autorisations d’accès**, spécifiez les autorisations d’accès sur la connexion de données.  
  
     Pour plus d’informations sur les propriétés avancées d’initialisation, reportez-vous à la documentation fournie avec chaque fournisseur OLE DB.  
  
 **All**  
     Cet onglet affiche un résumé des propriétés d’initialisation pour la source de données et de la connexion que vous avez spécifié. Vous pouvez modifier ces valeurs.  
  
     Cliquez sur **OK** à terminer. Le **sélectionner un objet de base de données** boîte de dialogue s’affiche. Dans cette boîte de dialogue, sélectionnez la table, une vue ou une procédure stockée que le consommateur doit utiliser.  
  
 `Class`  
 Après avoir sélectionné une source de données, cette zone est remplie avec un nom de classe par défaut basé sur la table ou la procédure stockée que vous avez sélectionné (voir **sélectionner une source de données** ci-dessous). Vous pouvez modifier le nom de classe.  
  
 **fichier .h**  
 Après avoir sélectionné une source de données, cette zone est remplie avec un nom de classe d’en-tête par défaut basé sur la table ou la procédure stockée que vous avez sélectionnée (consultez **sélectionner une source de données** ci-dessous). Vous pouvez modifier le nom du fichier d’en-tête ou sélectionner un fichier d’en-tête existant.  
  
 **Par attributs**  
 Cette option spécifie si l’Assistant va créer des classes de consommateur à l’aide d’attributs ou déclarations de modèle. Lorsque vous sélectionnez cette option, l’Assistant utilise les attributs au lieu des déclarations de modèle (il s’agit de l’option par défaut). Lorsque vous désélectionnez cette option, l’Assistant utilise des déclarations de modèle plutôt que des attributs.  
  
-   Si vous sélectionnez un consommateur **Type** de Table, l’Assistant utilise le `db_source` et **db_table** pour créer la table et l’accesseur de tableau de déclarations de classe d’attributs et utilise **db_column** pour créer le mappage de colonnes, par exemple :  
  
 ``` 
 // Inject table class and table accessor class declarations  
 [db_source("<initialization_string>"), db_table("dbo.Orders")]  
 ... 
 // Column map  
 [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;  
 [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];  
 ...  
 ```  
  
     au lieu d’utiliser la `CTable` classe de modèle pour déclarer la table et classe d’accesseur de table et les macros BEGIN_COLUMN_MAP et END_COLUMN_MAP pour créer le mappage de colonnes, par exemple :  
  
 ``` 
 // Table accessor class  
    class COrdersAccessor; *// Table class  
    class COrders : public CTable<CAccessor<COrdersAccessor>>;  
 ... 
 // Column map  
    BEGIN_COLUMN_MAP(COrderDetailsAccessor) 
    COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)  
    COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)  
 ...  
    END_COLUMN_MAP() 
 ```  
  
-   Si vous sélectionnez un consommateur **Type** de commande, l’Assistant utilise le `db_source` et **db_command** d’attributs et utilise **db_column** pour créer le mappage de colonnes, par exemple :  
  
 ```  
 [db_source("<initialization_string>"), db_command("SQL_command")]  
 ... 
 // Column map using db_column is the same as for consumer type of 'table'  
 ```  
  
     au lieu d’utiliser la commande et les déclarations de classes accesseur de commande dans le fichier .h de la classe de commande, par exemple :  
  
 ```  
    Command accessor class:  
    class CListOrdersAccessor;  
    Command class:  
    class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;  
 ... 
 // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
 // for consumer type of 'table'  
 ```  
  
 Consultez la page [mécanismes de base des attributs](../../windows/basic-mechanics-of-attributes.md) pour plus d’informations.  
  
 **Type**  
 Sélectionnez une de ces cases d’option pour spécifier si la classe de consommateur est dérivée de `CTable` ou `CCommand` (valeur par défaut).  
  
 **Table**  
 Sélectionnez cette option si vous souhaitez utiliser `CTable` ou **db_table** pour créer la table et l’accesseur de tableau de déclarations de classe.  
  
 **Commande**  
 Sélectionnez cette option si vous souhaitez utiliser `CCommand` ou **db_command** pour créer la commande et l’accesseur de commande de déclarations de classe. Il s’agit de la sélection par défaut.  
  
 **Prise en charge**  
 Activez les cases à cocher pour spécifier les types de mises à jour pour être prise en charge par le consommateur (la valeur par défaut est none). Chaque élément suivant définira [DBPROP_IRowsetChange](https://msdn.microsoft.com/library/ms715892.aspx) et les entrées appropriées pour [DBPROP_UPDATABILITY](https://msdn.microsoft.com/library/ms722676.aspx) dans le jeu de carte.  
  
 **Modification**  
 Spécifie que le consommateur prend en charge les mises à jour des données de ligne dans l’ensemble de lignes.  
  
 **Insérer**  
 Spécifie que le consommateur prend en charge l’insertion de lignes dans l’ensemble de lignes.  
  
 **Supprimer**  
 Spécifie que le consommateur prend en charge la suppression de lignes à partir de l’ensemble de lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Consommateur OLE DB ATL](../../atl/reference/adding-an-atl-ole-db-consumer.md)   
 [Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Chaînes de connexion et des liaisons de données (OLE DB)](https://msdn.microsoft.com/library/ms718376.aspx)

