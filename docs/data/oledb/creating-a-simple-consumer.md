---
title: Création d’un consommateur Simple | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 711aaaff2bc4e012ba4c4ef78465f06c51b9d307
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098522"
---
# <a name="creating-a-simple-consumer"></a>Création d'un consommateur simple
Utilisez l’Assistant Projet ATL et l’Assistant Consommateur OLE DB ATL pour générer un consommateur des modèles OLE DB.  
  
#### <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>Pour créer une application console destinée à un consommateur OLE DB  
  
1.  Dans le menu **Fichier** , cliquez sur **Nouveau**, puis sur **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Dans le volet Types de projets, cliquez sur le **projets Visual C++** dossier, puis cliquez sur le **projet Win32** icône dans le volet Modèles. Dans le **nom** , entrez le nom de votre projet, par exemple, **MyCons**.  
  
3.  Cliquez sur **OK**.  
  
     L’Assistant Projet Win32 s’affiche.  
  
4.  Sur le **paramètres de l’Application** page, sélectionnez **application Console**, puis sélectionnez **ajouter la prise en charge ATL**.  
  
5.  Cliquez sur **Terminer** pour fermer l’Assistant et générer le projet.  
  
 Ensuite, utilisez l’Assistant Consommateur OLE DB ATL pour ajouter un objet consommateur OLE DB.  
  
#### <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>Pour créer un consommateur avec l’Assistant Consommateur OLE DB ATL  
  
1.  Dans l’affichage de classes, cliquez sur le `MyCons` projet.  
  
2.  Dans le menu contextuel, cliquez sur **ajouter**, puis cliquez sur **ajouter une classe**.  
  
     Le **ajouter une classe** boîte de dialogue s’affiche.  
  
3.  Dans le volet des catégories, cliquez sur **Visual C++**, cliquez sur le **consommateur OLE DB ATL** icône dans le volet Modèles, puis cliquez sur **ouvrir**.  
  
     L’Assistant Consommateur OLE DB ATL s’affiche.  
  
4.  Cliquez sur le **Source de données** bouton.  
  
     Le **propriétés des liaisons de données** boîte de dialogue s’affiche.  
  
5.  Dans le **propriétés des liaisons de données** boîte de dialogue zone, procédez comme suit :  
  
    -   Sur le **fournisseur** onglet, spécifiez un fournisseur OLE DB.  
  
    -   Sur le **connexion** onglet, spécifiez le nom du serveur, ID de connexion et mot de passe pour votre source de données et la base de données sur le serveur.  
  
    > [!NOTE]
    >  Il existe un problème de sécurité avec le **autoriser l’enregistrement du mot de passe** fonctionnalité de la **propriétés des liaisons de données** boîte de dialogue. Dans **entrer des informations pour vous connecter au serveur**, il existe deux boutons radio : **la sécurité intégrée de Windows NT d’utilisation** et **utiliser un nom d’utilisateur spécifique et un mot de passe**.  
  
    > [!NOTE]
    >  Si vous sélectionnez **utiliser un nom d’utilisateur spécifique et un mot de passe**, vous avez la possibilité d’enregistrer le mot de passe (à l’aide de la **autoriser l’enregistrement du mot de passe** case à cocher) ; Cependant, cette option n’est pas sécurisée. Il est recommandé de sélectionner **la sécurité intégrée de Windows NT d’utilisation**; cette option utilise Windows NT pour vérifier votre identité.  
  
    > [!NOTE]
    >  Si vous ne pouvez pas utiliser la sécurité intégrée de Windows NT, vous devez utiliser une application de couche intermédiaire pour inviter l’utilisateur pour le mot de passe ou pour stocker le mot de passe dans un emplacement avec les mécanismes de sécurité pour aider à protéger (et non dans le code source).  
  
     Après avoir sélectionné le fournisseur et autres paramètres, cliquez sur **tester la connexion** pour vérifier les sélections effectuées dans les pages de boîte de dialogue précédente. Si le **résultats** zone rapports `Test connection succeeded`, cliquez sur **OK** pour créer la liaison de données.  
  
     Le **sélectionner un objet de base de données** boîte de dialogue s’affiche.  
  
6.  Utilisez le contrôle d’arborescence pour sélectionner une table, une vue ou une procédure stockée. Pour les besoins de cette procédure, sélectionnez la table Products de la base de données Northwind.  
  
7.  Cliquez sur **OK**. Cela vous renvoie à l’Assistant Consommateur OLE DB ATL.  
  
8.  L’Assistant renseigne les noms de `Class` et **fichier .h** basé sur le nom de la table, vue ou procédure stockée que vous avez sélectionné. Vous pouvez modifier ces noms si vous le souhaitez.  
  
9. Désactivez le **avec attributs** case à cocher pour que l’Assistant crée le code de consommateur à l’aide de [classes de modèles OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) au lieu de la valeur par défaut [attributs du consommateur OLE DB](../../windows/ole-db-consumer-attributes.md).  
  
10. Sous **Type**, sélectionnez **commande**.  
  
     L’Assistant crée un [CCommand](../../data/oledb/ccommand-class.md)-consommateur basé sur si vous sélectionnez **commande** ou un [CTable](../../data/oledb/ctable-class.md)-consommateur basé sur si vous sélectionnez **Table**. La classe de table ou de la commande est appelée après l’objet sélectionné, mais vous pouvez modifier le nom.  
  
11. Sous **prise en charge**, laissez le **modification**, **insérer**, et **supprimer** cases à cocher désactivées.  
  
     Sélectionnez le **modification**, **insérer**, et **supprimer** cases à cocher pour prendre en charge la modification, l’insertion et la suppression d’enregistrements dans l’ensemble de lignes, si nécessaire. Pour plus d’informations sur l’écriture de données pour les données de stockage, consultez [mise à jour des ensembles de lignes de](../../data/oledb/updating-rowsets.md).  
  
12. Cliquez sur **Terminer** pour créer le consommateur.  
  
 L’Assistant génère une classe de commande et une classe d’enregistrement utilisateur, comme indiqué dans [Consumer Wizard-Generated Classes](../../data/oledb/consumer-wizard-generated-classes.md). La classe de commande aura le nom que vous avez entré dans le `Class` zone dans l’Assistant (dans ce cas, `CProducts`), et la classe d’enregistrement utilisateur aura un nom sous la forme «*ClassName*accesseur » (dans ce cas, `CProductsAccessor`).  
  
> [!NOTE]
>  L’Assistant met la ligne suivante dans Products.h :  
  
```  
#error Security Issue: The connection string may contain a password  
```  
  
> [!NOTE]
>  Cette ligne empêche l’application de consommateur de la compilation et vous rappelle de vérifier votre chaîne de connexion pour les mots de passe codés en dur. Après avoir vérifié votre chaîne de connexion, vous pouvez supprimer cette ligne de code.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un consommateur OLE DB en utilisant l’Assistant](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)