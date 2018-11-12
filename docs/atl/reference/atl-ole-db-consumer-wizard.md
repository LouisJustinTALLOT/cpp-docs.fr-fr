---
title: Assistant Consommateur OLEDB ATL
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.consumer.overview
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- connection strings [C++], OLE DB consumers
- ATL OLE DB Consumer Wizard
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
ms.openlocfilehash: 835b3e6246741c3859f51e017686531f450db194
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499565"
---
# <a name="atl-ole-db-consumer-wizard"></a>Assistant Consommateur OLEDB ATL

Cet Assistant définit une classe de consommateur OLE DB avec les liaisons de données nécessaire pour accéder à la source de données spécifié via le fournisseur OLE DB spécifié.

> [!NOTE]
> Cet Assistant vous oblige à cliquer sur le **Source de données** pour sélectionner une source de données avant d’entrer des noms dans le `Class` et **fichier .h** champs.

## <a name="uielement-list"></a>Liste des éléments d’interface

- **Source de données**

   Le **Source de données** bouton vous permet de définir la source de données spécifié à l’aide du fournisseur OLE DB spécifié. Lorsque vous cliquez sur ce bouton, le **propriétés des liaisons de données** boîte de dialogue s’affiche. Pour plus d’informations sur la création de chaînes de connexion et le **propriétés des liaisons de données** boîte de dialogue, consultez [Data Link API Overview](/previous-versions/windows/desktop/ms718102) dans la documentation du SDK Windows.

   Les informations supplémentaires suivantes décrivent les onglets de la **propriétés des liaisons de données** boîte de dialogue.

   - **Fournisseur** onglet

      Sélectionnez un fournisseur approprié pour gérer la connexion à la source de données. Le type de fournisseur est généralement déterminé par le type de base de données à laquelle vous vous connectez. Cliquez sur le **suivant** bouton ou cliquez sur le **connexion** onglet.

   - **Connexion** onglet

      Le contenu de cet onglet varie selon le fournisseur sélectionné. Bien qu’il existe de nombreux types de fournisseurs, cette section traite des connexions pour les deux plus courants : données SQL et ODBC. Les autres sont des variations similaires sur les champs décrits ici.

      Pour les données SQL :

      1. **Sélectionnez ou entrez un nom de serveur :** cliquez sur le menu de liste déroulante pour afficher tous les serveurs de données inscrites sur le réseau, puis sélectionnez un.

      1. **Entrez les informations pour vous connecter au serveur :** Entrez un nom d’utilisateur et le mot de passe pour ouvrir une session le serveur de données.

         > [!NOTE]
         > Il existe un problème de sécurité avec la fonctionnalité « Autoriser l’enregistrement du mot de passe » de la boîte de dialogue Propriétés des liaisons de données. Dans « Entrez les informations pour vous connecter au serveur », il existe deux cases d’option :
         >
         > - **Utiliser la sécurité intégrée de Windows NT**
         > - **Utiliser un nom d’utilisateur spécifique et un mot de passe**
         >
         > Si vous sélectionnez **utiliser un nom d’utilisateur spécifique et un mot de passe**, vous avez la possibilité d’enregistrer le mot de passe (à l’aide de la case à cocher « Autoriser l’enregistrement du mot de passe ») ; Toutefois, cette option n’est pas sécurisée. Il est recommandé de sélectionner **utilisez Windows NT la sécurité intégrée**; cette option est sécurisée, car il chiffre le mot de passe.
         > Il peut y avoir des situations dans lesquelles vous souhaitez sélectionner « Autoriser l’enregistrement du mot de passe ». Par exemple, si vous lancez une bibliothèque avec une solution de base de données privée, vous devez pas accéder directement à la base de données mais à la place utiliser une application de couche intermédiaire pour vérifier que l’utilisateur (via les schémas d’authentification que vous choisissez), puis limiter le tri des données disponible pour l’utilisateur.

      1. **Sélectionnez la base de données sur le serveur :** cliquez sur le menu de liste déroulante pour afficher les inscrits toutes les bases de données sur le serveur de données, puis sélectionnez un.

         \- ou -

         **Attacher un fichier de base de données comme un nom de base de données :** spécifier un fichier à utiliser comme la base de données ; entrez le chemin d’accès explicite.

      Pour les données ODBC :

      1. **Spécifiez la source de données :** vous pouvez utiliser un nom de source de données ou une chaîne de connexion.

         **Nom de source de données utilisation :** cette liste déroulante affiche les sources de données inscrites sur votre ordinateur. Vous pouvez définir des sources de données à l’aide de l’administrateur de sources de données ODBC

         \- ou -

         **Utiliser la chaîne de connexion :** Entrez une chaîne de connexion que vous avez déjà obtenu, ou cliquez sur le **Build** bouton ; le **sélectionner une Source de données** boîte de dialogue s’affiche. Sélectionnez une source de données de fichier ou de la machine et cliquez sur **OK**.

         > [!NOTE]
         > Vous pouvez obtenir une chaîne de connexion en affichant les propriétés d’une connexion existante dans **Explorateur de serveurs**, ou vous pouvez créer une connexion en double-cliquant sur **ajouter une connexion** dans **Server Explorer**.

      1. **Entrez les informations pour vous connecter au serveur :** Entrez un nom d’utilisateur et le mot de passe pour ouvrir une session le serveur de données.

      1. Entrez le catalogue initial à utiliser.

      1. Cliquez sur **tester la connexion**; si le test réussit, cliquez sur **OK**. Si ce n’est pas le cas, vérifiez vos informations d’ouverture de session, essayez une autre base de données ou un autre serveur de données.

   - **Advanced** onglet

      **Paramètres réseau :** spécifier le **au niveau d’emprunt d’identité** (le niveau d’emprunt d’identité que le serveur est autorisé à utiliser lors de l’emprunt d’identité du client ; correspond directement à des niveaux d’emprunt d’identité RPC) et  **Niveau de protection** (le niveau de protection des données envoyées entre le client et le serveur ; correspond directement à des niveaux de protection RPC).

      **Autre :** dans **Connect timeout**, spécifiez le nombre de secondes d’inactivité autorisée avant un délai d’expiration se produit. Dans **autorisations d’accès**, spécifiez les autorisations d’accès sur la connexion de données.

       Pour plus d’informations sur les propriétés avancées d’initialisation, reportez-vous à la documentation fournie avec chaque fournisseur OLE DB.

   - **Tous les** onglet

      Cet onglet affiche un résumé des propriétés d’initialisation pour la source de données et de la connexion que vous avez spécifié. Vous pouvez modifier ces valeurs.

   Cliquez sur **OK** se termine. Le **sélectionner un objet de base de données** boîte de dialogue s’affiche. Dans cette boîte de dialogue, sélectionnez la table, une vue ou une procédure stockée que le consommateur doit utiliser.

- **Classe**

   Après avoir sélectionné une source de données, cette zone est remplie avec un nom de classe par défaut basé sur la table ou la procédure stockée que vous avez sélectionnée (consultez **sélectionner une source de données** ci-dessous). Vous pouvez modifier le nom de classe.

- **Fichier .h**

   Après avoir sélectionné une source de données, cette zone est remplie avec un nom de classe d’en-tête par défaut basé sur la table ou la procédure stockée que vous avez sélectionnée (consultez **sélectionner une source de données** ci-dessous). Vous pouvez modifier le nom du fichier d’en-tête ou sélectionnez un fichier d’en-tête existant.

- **Attribué**

   Cette option spécifie si l’Assistant va créer des classes de consommateur à l’aide d’attributs ou déclarations de modèle. Lorsque vous sélectionnez cette option, l’Assistant utilise les attributs au lieu de déclarations de modèle (il s’agit de l’option par défaut). Lorsque vous désélectionnez cette option, l’Assistant utilise des déclarations de modèle au lieu d’attributs.

   - Si vous sélectionnez un consommateur **Type** de **Table**, l’Assistant utilise le `db_source` et `db_table` attributs permettant de créer la table et l’accesseur de la table des déclarations de classe et utilise `db_column` pour créer le mappage de colonne. Par exemple, il crée ce mappage :

        ```cpp
        // Inject table class and table accessor class declarations
        [db_source("<initialization_string>"), db_table("dbo.Orders")]
        ...
        // Column map
        [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
        [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
        ...
        ```

      au lieu d’utiliser la `CTable` classe de modèle pour déclarer la table et classe d’accesseur de table et les macros BEGIN_COLUMN_MAP et END_COLUMN_MAP pour créer le mappage de colonne, comme dans cet exemple :

        ```cpp
        // Table accessor class
            class COrdersAccessor; // Table class
            class COrders : public CTable<CAccessor<COrdersAccessor>>;
        // ...
        // Column map
            BEGIN_COLUMN_MAP(COrderDetailsAccessor)
                COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)
                COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)
                // ...
            END_COLUMN_MAP()
        ```

   - Si vous sélectionnez un consommateur **Type** de **commande**, l’Assistant utilise le `db_source` et `db_command` des attributs et utilise `db_column` pour créer le mappage de colonnes. Par exemple, il crée ce mappage :

        ```cpp
        [db_source("<initialization_string>"), db_command("SQL_command")]
        ...
        // Column map using db_column is the same as for consumer type of 'table'
        ```

      au lieu d’utiliser la commande et les déclarations de classe d’accesseur commande dans le fichier .h de la classe de commande, par exemple :

        ```cpp
        // Command accessor class:
            class CListOrdersAccessor;
        // Command class:
            class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
        // ...
        // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
        // for consumer type of 'table'
        ```

      Consultez [mécanismes de base des attributs](../../windows/basic-mechanics-of-attributes.md) pour plus d’informations.

- **Type**

   Sélectionnez une de ces cases d’option pour spécifier si la classe de consommateur est dérivée de `CTable` ou `CCommand` (valeur par défaut).

   - **Table**

      Sélectionnez cette option si vous souhaitez utiliser `CTable` ou `db_table` pour créer la table et l’accesseur de la table de déclarations de classe.

   - **Commande**

      Sélectionnez cette option si vous souhaitez utiliser `CCommand` ou `db_command` pour créer la commande et un accesseur de commande de déclarations de classe. Il s’agit de la sélection par défaut.

- **Prise en charge**

   Sélectionnez les cases à cocher pour spécifier les types de mises à jour pour être pris en charge dans le consommateur (la valeur par défaut est none). Chacun des éléments suivants définira [DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892) et les entrées appropriées pour [DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676) dans la jeu de propriétés carte.

   - **Modification**

      Spécifie que le consommateur prend en charge les mises à jour des données de ligne dans l’ensemble de lignes.

   - **Insert**

      Spécifie que le consommateur prend en charge l’insertion de lignes dans l’ensemble de lignes.

   - **Supprimer**

      Spécifie que le consommateur prend en charge la suppression de lignes à partir de l’ensemble de lignes.

## <a name="see-also"></a>Voir aussi

[Consommateur ATL OLE DB](../../atl/reference/adding-an-atl-ole-db-consumer.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Chaînes de connexion et des liaisons de données (OLE DB)](/previous-versions/windows/desktop/ms718376)
