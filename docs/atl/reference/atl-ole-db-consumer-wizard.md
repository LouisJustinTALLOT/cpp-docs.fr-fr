---
title: Assistant Consommateur OLEDB ATL
ms.date: 07/02/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
ms.openlocfilehash: 16b2863bc3919edadeef29691c4588838010d9dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319272"
---
# <a name="atl-ole-db-consumer-wizard"></a>Assistant Consommateur OLEDB ATL

::: moniker range="vs-2019"

Cet Assistant n’est pas disponible dans Visual Studio 2019 et ultérieur.

::: moniker-end

::: moniker range="<=vs-2017"

Cet Assistant définit une classe de consommateur OLE DB avec les liaisons de données nécessaires pour accéder à la source de données spécifiée via le fournisseur OLE DB spécifié.

> [!NOTE]
> Cet Assistant nécessite que vous cliquiez sur le bouton **Source de données** pour sélectionner une source de données avant d’entrer des noms dans les champs `Class` et **fichier .h**.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

- **Source de données**

   Le bouton **Source de données** vous permet de configurer la source de données spécifiée à l’aide du fournisseur OLE DB spécifié. Lorsque vous cliquez sur ce bouton, la boîte de dialogue **Propriétés des liaisons de données** s’affiche. Pour plus d’informations sur la création de chaînes de connexion et la boîte de dialogue **Propriétés des liaisons de données**, consultez [Data Link API Overview](/previous-versions/windows/desktop/ms718102(v=vs.85)) (Présentation de la liaison de données) dans la documentation du SDK Windows.

   Les informations supplémentaires suivantes décrivent les onglets de la boîte de dialogue **Propriétés des liaisons de données**.

  - Onglet **Fournisseur**

      Sélectionnez un fournisseur approprié pour gérer la connexion à la source de données. Le type de fournisseur est généralement déterminé par le type de la base de données à laquelle vous vous connectez. Cliquez sur le bouton **Suivant** ou sur l’onglet **Connexion**.

  - **Onglet de connexion**

      Le contenu de cet onglet varie en fonction du fournisseur sélectionné. Bien qu’il existe de nombreux types de fournisseurs, cette section couvre les connexions pour les deux données les plus courantes : SQL et ODBC. Les autres présentent des variations des champs décrits ici.

      Pour les données SQL :

      1. **Sélectionnez ou entrez un nom de serveur :** Cliquez sur le menu de la liste d’abandon pour afficher tous les serveurs de données enregistrés sur le réseau, et sélectionnez-en un.

      1. **Entrez les informations pour vous connecter au serveur :** Entrez un nom d’utilisateur et un mot de passe pour vous connecter au serveur de données.

         > [!NOTE]
         > Il existe un problème de sécurité avec la fonctionnalité « Autoriser l’enregistrement du mot de passe » de la boîte de dialogue Propriétés des liaisons de données. Dans « Entrez des informations pour vous connecter au serveur », deux cases d’option sont disponibles :
         >
         > - **Utiliser la sécurité intégrée de Windows NT**
         > - **Utiliser un nom d'utilisateur et un mot de passe spécifiques**
         >
         > Si vous sélectionnez **Utiliser un nom d’utilisateur spécifique et un mot de passe**, vous avez la possibilité d’enregistrer le mot de passe (à l’aide de la case à cocher « Autoriser l’enregistrement du mot de passe ») ; néanmoins, cette option n’est pas sûre. Nous vous recommandons plutôt de sélectionner l’option **Utiliser la sécurité intégrée de Windows NT**, qui crypte le mot de passe, assurant sa sécurité.
         > Dans certaines situations, vous souhaiterez quand même sélectionner « Autoriser l’enregistrement du mot de passe ». Par exemple, si vous publiez une bibliothèque avec une solution de base de données privée, vous ne devez pas accéder à la base de données directement, mais plutôt utiliser une application intermédiaire pour identifier l’utilisateur (via le schéma d’authentification de votre choix), puis limiter les données disponibles pour l’utilisateur.

      1. **Sélectionnez la base de données sur le serveur :** Cliquez sur le menu de la liste d’abandon pour afficher toutes les bases de données enregistrées sur le serveur de données, et sélectionnez-en une.

         \- ou -

         **Joindre un fichier de base de données comme nom de base de données :** Spécifiez un fichier à utiliser comme base de données; entrer dans le nom de chemin explicite.

      Pour les données ODBC :

      1. **Spécifier la source de données :** Vous pouvez utiliser un nom source de données ou une chaîne de connexion.

         **Utilisez le nom de source de données :** Cette liste d’abandon affiche les sources de données enregistrées dans votre machine. Vous pouvez configurer des sources de données à l’avance à l’aide de l’administrateur de sources de données ODBC

         \- ou -

         **Utiliser la chaîne de connexion :** Entrez une chaîne de connexion que vous avez déjà obtenue, soit cliquez sur le bouton **Build** ; la boîte de dialogue **Select Data Source** apparaît. Sélectionnez une source de données de fichier ou de machine et cliquez sur **OK**.

         > [!NOTE]
         > Vous pouvez obtenir une chaîne de connexion en affichant les propriétés d’une connexion existante dans l’**Explorateur de serveurs**, ou vous pouvez créer une connexion en double-cliquant sur **Ajouter une connexion** dans l’**Explorateur de serveurs**.

      1. **Entrez les informations pour vous connecter au serveur :** Entrez un nom d’utilisateur et un mot de passe pour vous connecter au serveur de données.

      1. Saisissez le catalogue initial à utiliser.

      1. Cliquez sur **Tester la connexion** ; si le test réussit, cliquez sur **OK**. Si ce n’est pas le cas, vérifiez vos informations d’ouverture de session, ou bien essayez une autre base de données ou un autre serveur de données.

  - **Onglet avancé**

      **Paramètres réseau :** Spécifiez le **niveau d’usurpation d’identité** (le niveau d’usurpation d’identité que le serveur est autorisé à utiliser lors de l’usurpation d’identité du client; correspond directement aux niveaux d’usurpation d’identité RPC) et le niveau de **protection** (niveau de protection des données envoyées entre le client et le serveur; correspond directement aux niveaux de protection RPC).

      **Autres:** Dans **Connect timeout**, spécifiez le nombre de secondes de temps d’inactivité autorisé avant un délai d’attente. Dans les **Autorisations d’accès**, spécifiez les autorisations d’accès pour la connexion de données.

      Pour plus d’informations sur les propriétés d’initialisation avancées, reportez-vous à la documentation fournie avec chaque fournisseur OLE DB spécifique.

  - Onglet **Tous**

      Cet onglet affiche un résumé des propriétés d’initialisation pour la source de données et la connexion que vous avez spécifiées. Vous pouvez modifier ces valeurs.

      Cliquez sur **OK** pour terminer. La boîte de dialogue **Sélectionner l’objet de base de données** s’affiche. Dans cette boîte de dialogue, sélectionnez la table, la vue ou la procédure stockée que le consommateur doit utiliser.

- **Classe**

   Après avoir sélectionné une source de données, cette zone est remplie avec un nom de classe par défaut basé sur la table ou la procédure stockée que vous avez sélectionnée (consultez **Sélectionner une source de données** ci-dessous). Vous pouvez modifier le nom de classe.

- **Fichier .h**

   Après avoir sélectionné une source de données, cette zone est remplie avec un nom de classe d’en-tête par défaut basé sur la table ou la procédure stockée que vous avez sélectionnée (consultez **Sélectionner une source de données** ci-dessous). Vous pouvez modifier le nom de ce fichier d’en-tête ou sélectionner un fichier d’en-tête existant.

- **Avec attributs**

   Cette option spécifie si l’Assistant va créer des classes de consommateur à l’aide d’attributs ou de déclarations de modèle. Lorsque vous sélectionnez cette option, l’Assistant utilise des attributs plutôt que des déclarations de modèle (il s’agit de l’option par défaut). Lorsque vous décochez cette option, l’Assistant utilise des déclarations de modèle à la place des attributs.

  - Si vous sélectionnez un **Type** de **Table** pour le consommateur, l’Assistant utilise les attributs `db_source` et `db_table` pour créer la table et les déclarations de classe d’accesseur de la table, et utilise `db_column` pour créer le mappage de colonnes. Par exemple, il crée ce mappage :

    ```cpp
    // Inject table class and table accessor class declarations
    [db_source("<initialization_string>"), db_table("dbo.Orders")]
    ...
    // Column map
    [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
    [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
    ...
    ```

     au lieu d’utiliser la classe de modèle `CTable` pour déclarer la table et la classe d’accesseur de table, ainsi que les macros BEGIN_COLUMN_MAP et END_COLUMN_MAP pour créer le mappage de colonne, comme dans cet exemple :

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

  - Si vous sélectionnez un **Type** de **Commande** pour le consommateur, l’Assistant utilise les attributs `db_source` et `db_command`, et utilise `db_column` pour créer le mappage de colonnes. Par exemple, il crée ce mappage :

    ```cpp
    [db_source("<initialization_string>"), db_command("SQL_command")]
    ...
    // Column map using db_column is the same as for consumer type of 'table'
    ```

     au lieu d’utiliser la commande et les déclarations de classe d’accesseur de la commande dans le fichier .h de la classe de commande, par exemple :

    ```cpp
    // Command accessor class:
        class CListOrdersAccessor;
    // Command class:
        class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
    // ...
    // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
    // for consumer type of 'table'
    ```

     Consultez [Mécanismes de base des attributs](../../windows/basic-mechanics-of-attributes.md) pour plus d’informations.

- **Type**

   Sélectionnez l’une de ces cases d’option pour spécifier si la classe de consommateur est dérivée de `CTable` ou `CCommand` (valeur par défaut).

  - **Table**

      Sélectionnez cette option si vous souhaitez utiliser `CTable` ou `db_table` pour créer la table et les déclarations de classe de l’accesseur de table.

  - **Commande**

      Sélectionnez cette option si vous souhaitez utiliser `CCommand` ou `db_command` pour créer la commande et les déclarations de classe de l’accesseur de commande. Il s'agit de la sélection par défaut.

- **Support**

   Sélectionnez les cases à cocher pour spécifier les types de mises à jour devant être prises en charge dans le consommateur (la valeur par défaut est aucun). Chacun des éléments suivants configure [DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892(v=vs.85)) et les entrées appropriées pour [DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676(v=vs.85)) dans le mappage d’ensemble des propriétés.

  - **changement**

      Spécifie que le consommateur prend en charge les mises à jour des données de ligne dans l’ensemble de lignes.

  - **Insérer**

      Spécifie que le consommateur prend en charge l’insertion de lignes dans l’ensemble de lignes.

  - **Supprimer**

      Spécifie que le consommateur prend en charge la suppression de lignes dans l’ensemble de lignes.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Consommateur ATL OLE DB](../../atl/reference/adding-an-atl-ole-db-consumer.md)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Chaînes de connexion et liaisons de données (OLE DB)](/previous-versions/windows/desktop/ms718376(v=vs.85))
