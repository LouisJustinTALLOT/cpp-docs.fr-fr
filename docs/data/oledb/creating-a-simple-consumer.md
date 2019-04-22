---
title: Création d'un consommateur simple
ms.date: 11/06/2018
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
ms.openlocfilehash: 060a39a8436ff73900ebfaea7d1c882b9862ee7e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025128"
---
# <a name="creating-a-simple-consumer"></a>Création d'un consommateur simple

Utilisez le **Assistant Projet ATL** et **Assistant Consommateur OLE DB ATL** pour générer un consommateur des modèles OLE DB.

## <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>Pour créer une application de console pour un consommateur OLE DB

1. Dans le menu **Fichier** , cliquez sur **Nouveau**, puis sur **Projet**.

   La boîte de dialogue **Nouveau projet** s’affiche.

1. Dans le **Types de projets** volet, cliquez sur le **installé** > **Visual C++** > **Windows Desktop** dossier, puis cliquez sur le **Windows Desktop Assistant** icône dans le **modèles** volet. Dans le **nom** , entrez le nom de votre projet, par exemple, *MyCons*.

1. Cliquez sur **OK**.

   Le **projet de bureau Windows** Assistant s’affiche.

1. Sur le **paramètres d’Application** page, sélectionnez **application Console**, puis sélectionnez **ajouter des fichiers d’en-tête courants pour ATL**.

1. Cliquez sur **OK** pour fermer l’Assistant et générer le projet.

Ensuite, utilisez le **Assistant Consommateur OLE DB ATL** pour ajouter un objet du consommateur OLE DB.

## <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>Pour créer un consommateur avec l’Assistant Consommateur OLE DB ATL

1. Dans **l’Explorateur de solutions**, avec le bouton droit le `MyCons` projet.

1. Dans le menu contextuel, cliquez sur **ajouter**, puis cliquez sur **un nouvel élément**.

   La boîte de dialogue **Ajouter un nouvel élément** s’affiche.

1. Dans le **catégories** volet, cliquez sur **installé** > **Visual C++** > **ATL**, cliquez sur le **ATL OLEDB Consumer** icône dans le **modèles** volet, puis cliquez sur **ajouter**.

   Le **l’Assistant consommateur OLEDB ATL** s’affiche.

1. Cliquez sur le **Source de données** bouton.

   Le **propriétés des liaisons de données** boîte de dialogue s’affiche.

1. Dans le **propriétés des liaisons de données** boîte de dialogue zone, procédez comme suit :

   1. Sur le **fournisseur** onglet, spécifiez un fournisseur OLE DB.

   1. Sur le **connexion** onglet, spécifiez les informations requises, telles que le nom du serveur, nom d’utilisateur et mot de passe pour votre source de données et de la base de données sur le serveur.

      > [!NOTE]
      > Il existe un problème de sécurité avec le **autoriser l’enregistrement du mot de passe** fonctionnalité de la **propriétés des liaisons de données** boîte de dialogue. Dans **Entrez des informations pour vous connecter au serveur**, il existe deux cases d’option : **Utilisez Windows NT de la sécurité intégrée** et **utiliser un nom d’utilisateur spécifique et un mot de passe**.

      > [!NOTE]
      > Si vous sélectionnez **utiliser un nom d’utilisateur spécifique et un mot de passe**, vous avez la possibilité d’enregistrer le mot de passe (à l’aide de la **autoriser l’enregistrement du mot de passe** case à cocher) ; Toutefois, cette option n’est pas sécurisée. Il est recommandé de sélectionner **utilisez Windows NT la sécurité intégrée**; cette option utilise Windows NT pour vérifier votre identité.

      > [!NOTE]
      > Si vous ne pouvez pas utiliser la sécurité intégrée de Windows NT, vous devez utiliser une application de couche intermédiaire pour inviter l’utilisateur pour le mot de passe ou pour stocker le mot de passe dans un emplacement avec les mécanismes de sécurité pour aider à protéger (et non dans le code source).

   1. Après avoir sélectionné votre fournisseur et autres paramètres, cliquez sur **tester la connexion** pour vérifier les sélections opérées dans les pages de boîte de dialogue précédente. Si le **résultats** zone rapports `Test connection succeeded`, cliquez sur **OK** pour créer la liaison de données.

   Le **sélectionner un objet de base de données** boîte de dialogue s’affiche.

1. Utilisez le contrôle d’arborescence pour sélectionner une table, une vue ou une procédure stockée. Pour cet exemple, sélectionnez le `Products` table à partir de la `Northwind` base de données.

1. Cliquez sur **OK**. Cela vous ramène à la **Assistant Consommateur OLE DB ATL**.

1. L’Assistant renseigne les noms de `Class` et **fichier .h** basé sur le nom de la table, vue ou procédure stockée que vous avez sélectionné. Vous pouvez modifier ces noms si vous le souhaitez.

1. Effacer la **avec attributs** case à cocher pour que l’Assistant crée le code de consommateur à l’aide [classes de modèles OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) au lieu de la valeur par défaut [attributs du consommateur OLE DB](../../windows/ole-db-consumer-attributes.md).

1. Sous **Type**, sélectionnez **commande**.

   L’Assistant crée un [CCommand](../../data/oledb/ccommand-class.md)-consommateur basé sur si vous sélectionnez **commande** ou un [CTable](../../data/oledb/ctable-class.md)-consommateur basé sur si vous sélectionnez **Table**. La classe de table ou de la commande est appelée après l’objet sélectionné, mais vous pouvez modifier le nom.

1. Sous **prise en charge**, laissez le **modification**, **insérer**, et **supprimer** cases à cocher désactivées.

   Sélectionnez le **modification**, **insérer**, et **supprimer** cases à cocher pour prendre en charge la modification, l’insertion et la suppression d’enregistrements dans l’ensemble de lignes. Pour plus d’informations sur l’écriture de données dans les données de stockage, consultez [ensembles de lignes de la mise à jour](../../data/oledb/updating-rowsets.md).

1. Cliquez sur **Terminer** pour créer le consommateur.

L’Assistant génère une classe de commande et une classe d’enregistrement utilisateur, comme indiqué dans [Consumer Wizard-Generated Classes](../../data/oledb/consumer-wizard-generated-classes.md). La classe de commande aura le nom que vous avez entré dans le `Class` zone dans l’Assistant (dans ce cas, `CProducts`), et la classe d’enregistrement utilisateur aura un nom sous la forme «*ClassName*accesseur » (dans ce cas, `CProductsAccessor`).

> [!NOTE]
> L’Assistant met la ligne suivante dans `Products.h`:

```cpp
#error Security Issue: The connection string may contain a password
```

> [!NOTE]
> Cette ligne empêche l’application consommateur à partir de la compilation et vous rappelle de vérifier votre chaîne de connexion pour les mots de passe codés en dur. Après avoir vérifié votre chaîne de connexion, vous pouvez supprimer cette ligne de code.

## <a name="see-also"></a>Voir aussi

[Création d’un consommateur OLE DB en utilisant l’Assistant](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
