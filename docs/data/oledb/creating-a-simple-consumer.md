---
title: Création d'un consommateur simple
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
ms.openlocfilehash: cc24df1f15d43c384e6bf3853766fad82cf51255
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707714"
---
# <a name="creating-a-simple-consumer"></a>Création d'un consommateur simple

::: moniker range="vs-2019"

L’Assistant Consommateur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et les versions ultérieures. Vous pouvez toujours ajouter la fonctionnalité manuellement. Pour plus d’informations, consultez [Création d’un consommateur sans utiliser l’Assistant](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=vs-2017"

Utilisez **l’Assistant Projet ATL** et **l’Assistant Consommateur OLE DB ATL** pour générer un consommateur de modèles OLE DB.

## <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>Pour créer une application de console pour un consommateur OLE DB

1. Dans le menu **Fichier** , cliquez sur **Nouveau**, puis sur **Projet**.

   La boîte de dialogue **Nouveau projet** s’affiche.

1. Dans le volet **Types de projet**, cliquez sur le dossier **Installé** > **Visual C++** > **Bureau Windows**, puis cliquez sur l’icône **Assistant Windows Desktop** du volet **Modèles**. Dans le champ **Nom**, entrez le nom de votre projet, par exemple, *MyCons*.

1. Cliquez sur **OK**.

   L’Assistant **Projet Windows Desktop** s’affiche.

1. Sur la page **Paramètres de l’application**, sélectionnez **Application console**, puis **Add common header files for ATL** (Ajouter des fichiers d’en-tête communs pour ATL).

1. Cliquez sur **OK** pour fermer l’Assistant et générer le projet.

Ensuite, utilisez **l’Assistant Consommateur OLE DB ATL** pour ajouter un objet de consommateur OLE DB.

## <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>Pour créer un consommateur avec l’Assistant Consommateur OLE DB ATL

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet `MyCons`.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Nouvel élément**.

   La boîte de dialogue **Ajouter un nouvel élément** s’affiche.

1. Dans le volet **Catégories**, cliquez sur **Installé** > **Visual C++** > **ATL**, puis cliquez sur l’icône **Consommateur OLE DB ATL** dans le volet **Modèles** et enfin, cliquez sur **Ajouter**.

   **L’Assistant Consommateur OLE DB ATL** s’affiche.

1. Cliquez sur le bouton **Source de données**.

   La boîte de dialogue **Propriétés des liaisons de données** apparaît alors.

1. Dans la boîte de dialogue **Propriétés des liaisons de données**, effectuez ce qui suit :

   1. Dans l’onglet **Fournisseur**, spécifiez un fournisseur OLE DB.

   1. Dans l’onglet **Connexion**, spécifiez les informations requises, telles que le nom du serveur, l’ID d’ouverture de session et le mot de passe de votre source de données et base de données sur le serveur.

      > [!NOTE]
      > Il existe un problème de sécurité avec la fonctionnalité **Autoriser l’enregistrement du mot de passe** de la boîte de dialogue **Propriétés des liaisons de données**. Dans **Entrez des informations pour vous connecter au serveur**, deux cases d’option sont disponibles : **Utiliser la sécurité intégrée de Windows NT** et **Utiliser un nom d’utilisateur et un mot de passe spécifiques**.

      > [!NOTE]
      > Si vous sélectionnez **Utiliser un nom d’utilisateur et un mot de passe spécifiques**, vous avez la possibilité d’enregistrer le mot de passe (à l’aide de la case à cocher **Autoriser l’enregistrement du mot de passe**) ; néanmoins, c’est option n’est pas la plus sûre. Nous vous recommandons plutôt de sélectionner l’option **Utiliser la sécurité intégrée de Windows NT**, qui utilise Windows NT pour vérifier votre identité.

      > [!NOTE]
      > Si vous ne pouvez pas utiliser la sécurité intégrée de Windows NT, vous devez utiliser une application de niveau intermédiaire pour inviter l’utilisateur à fournir son mot de passe ou pour stocker le mot de passe dans un emplacement avec des mécanismes de sécurité permettant de le protéger (plutôt que dans le code source).

   1. Après avoir sélectionné votre fournisseur et les autres paramètres, cliquez sur **Tester la connexion** pour vérifier les sélections effectuées dans les pages précédentes de la boîte de dialogue. Si le champ **Résultats** indique `Test connection succeeded`, cliquez sur **OK** pour créer la liaison de données.

   La boîte de dialogue **Sélectionner l’objet de base de données** s’affiche.

1. Utilisez le contrôle d’arborescence pour sélectionner une table, un affichage ou une procédure stockée. Pour cet exemple, sélectionnez la table `Products` de la base de données `Northwind`.

1. Cliquez sur **OK**. Cela vous renvoie vers **l’Assistant Consommateur OLE DB ATL**.

1. L’Assistant renseigne les noms de `Class` et du **fichier .h** en fonction du nom de la table, de l’affichage ou de la procédure stockée que vous avez sélectionnés. Vous pouvez modifier ces noms si vous le souhaitez.

1. Décochez la case **Avec attributs** pour que l’Assistant puisse créer le code du consommateur à l’aide des [classes du modèle OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md), plutôt qu’avec les [attributs de consommateur OLE DB](../../windows/ole-db-consumer-attributes.md) par défaut.

1. Sous **Type**, sélectionnez **Command**.

   L’Assistant crée un consommateur basé sur [CCommand](../../data/oledb/ccommand-class.md) si vous sélectionnez **Command** ou un consommateur basé sur [CTable](../../data/oledb/ctable-class.md) si vous sélectionnez **Table**. Le nom de la classe command ou table dépend de l’objet sélectionné, mais vous pouvez le modifier.

1. Sous **Prise en charge**, laissez les cases **Modifier**, **Insérer** et **Supprimer** décochées.

   Cochez les cases **Modifier**, **Insérer** et **Supprimer** pour prendre en charge la modification, l’insertion et la suppression des enregistrements dans l’ensemble de lignes. Pour plus d’informations sur l’écriture de données dans le magasin de données, consultez [Updating Rowsets](../../data/oledb/updating-rowsets.md) (Mise à jour des ensembles de lignes).

1. Cliquez sur **Terminer** pour créer le consommateur.

L’Assistant génère une classe command et une classe user record, comme indiqué dans [Classes de consommateur générées par l’Assistant](../../data/oledb/consumer-wizard-generated-classes.md). La classe command prend le nom que vous avez entré dans le champ `Class` (ici, `CProducts`), tandis que la classe user record prend un nom au format « *NomClasse*Accessor » (ici, `CProductsAccessor`).

> [!NOTE]
> L’Assistant place la ligne suivante dans `Products.h` :

```cpp
#error Security Issue: The connection string may contain a password
```

> [!NOTE]
> Cette ligne empêche l’application du consommateur d’effectuer des compilations et vous rappelle de vérifier votre chaîne de connexion pour les mots de passe codés en dur. Après avoir vérifié votre chaîne de connexion, vous pouvez supprimer cette ligne de code.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Création d’un consommateur OLE DB en utilisant l’Assistant](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
