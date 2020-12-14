---
description: 'En savoir plus sur : Assistant classe MFC'
title: Classe MFC (Assistant)
ms.date: 09/06/2019
f1_keywords:
- vc.wizards.classwizard
helpviewer_keywords:
- MFC Class Wizard
ms.assetid: 8b0dd867-5d07-4214-99be-2a1c1995e6d9
ms.openlocfilehash: ba82cabd13fb242f5201243cd9f06c44df8141ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219185"
---
# <a name="mfc-class-wizard"></a>Classe MFC (Assistant)

Utilisez l' **Assistant classe** pour créer des classes MFC ou ajouter des messages et des gestionnaires de messages à des classes existantes dans votre projet.

Il existe trois façons d’ouvrir l' **Assistant classe**:

- Dans le menu **projet** , choisissez **Assistant classe**.
- Tapez **CTRL**  >  **MAJ**  >  **X**.
- Dans **affichage de classes**, cliquez avec le bouton droit sur une classe ou le nœud du projet, puis choisissez **Assistant classe**.

![Assistant classe](media/class-wizard.png "Classe MFC (Assistant)")

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

- **Projet**

   Nom d’un projet dans votre solution.

   Vous pouvez sélectionner d’autres projets de votre solution dans la zone de liste déroulante.

- **Nom de la classe**

   Nom d’une classe dans votre projet.

   Lorsque vous sélectionnez une classe dans la liste nom de la **classe** , les données de la classe remplissent les contrôles dans l' **Assistant classe MFC**. Lorsque vous modifiez la valeur d’un contrôle, les données de la classe sélectionnée sont affectées.

- **Ajouter une classe**

   Vous permet d’ajouter une nouvelle classe à votre projet MFC.

- **Classe de base**

   Classe de base de la classe qui est affichée dans le nom de la **classe**.

- **Déclaration de classe**

   Classe dans laquelle la classe de **nom de classe** est déclarée.

   La zone **déclaration de classe** s’affiche uniquement si son nom diffère de celui de l’implémentation de la **classe**.

- **Ressource**

   ID de la ressource dans le **nom** de la classe, le cas échéant. Dans le cas contraire, la zone de **ressources** est vide.

- **Implémentation de classe**

   Nom du fichier qui contient l’implémentation de la classe dans le nom de la **classe**.

   Vous pouvez sélectionner un autre fichier d’implémentation en cliquant sur la flèche. Le tableau suivant répertorie les options disponibles.

   |Option|Description|
   |------------|-----------------|
   |**Ouvrir un fichier**|Quitte l’Assistant classe et ouvre le fichier d’implémentation de classe actuel.|
   |**Ouvrir le dossier conteneur**|Ouvre le dossier qui contient le fichier d’implémentation de classe actuel.|
   |**Copier le chemin d’accès complet dans le presse-papiers**|Copie le chemin d’accès du fichier d’implémentation actuel dans le presse-papiers.|

- **Commandes**

   Permet d’ajouter, de supprimer, de modifier ou de rechercher une commande et son gestionnaire de messages.

   Pour ajouter un gestionnaire, cliquez sur **Ajouter un gestionnaire** ou double-cliquez sur un élément dans la liste ID d' **objet** ou **messages** . Le nom, l’ID et le message de la fonction résultante s’affichent dans la liste des **fonctions membres** .

   Pour supprimer un gestionnaire, sélectionnez un élément dans la liste **fonctions membres** , puis cliquez sur **supprimer le gestionnaire**.

   Pour modifier un gestionnaire, double-cliquez sur l’élément correspondant dans la liste **fonctions membres** . Ou sélectionnez un élément dans la zone de liste, puis cliquez sur **modifier le code**.

- **Messages**

   Permet d’ajouter, de supprimer, de modifier ou de rechercher un message et son gestionnaire de messages.

   Pour ajouter un gestionnaire, cliquez sur **Ajouter un gestionnaire** ou double-cliquez sur un élément dans la liste **messages** .

   Pour ajouter un message personnalisé, cliquez sur **Ajouter un message personnalisé** ou appuyez sur la touche entrée, puis spécifiez des valeurs dans la boîte de dialogue **Ajouter un message personnalisé** . Dans cette boîte de dialogue, vous pouvez également sélectionner **message inscrit** pour gérer un message de fenêtre dont l’unicité est garantie dans tout le système d’exploitation.

- **Fonctions virtuelles**

   Permet d’ajouter, de supprimer, de modifier ou de rechercher une fonction virtuelle, ou une fonction virtuelle substituée.

- **Variables membres**

   Permet d’ajouter, de supprimer, de modifier ou de rechercher une variable membre.

- **Méthodes**

   Vous permet d’ajouter, de supprimer ou de rechercher une méthode, ainsi que d’accéder à la définition ou à la déclaration d’une méthode.

   Pour ajouter une méthode, cliquez sur **Ajouter une méthode**, puis spécifiez des valeurs dans la boîte de dialogue Ajouter une **méthode** .

   Pour supprimer une méthode, sélectionnez un élément dans la liste **méthodes** , puis cliquez sur **Supprimer la méthode**.

   Pour afficher une déclaration, sélectionnez un élément dans la liste **méthodes** , puis cliquez sur **atteindre la déclaration.**

   Pour afficher une définition, double-cliquez sur un élément dans la liste des **méthodes** . Ou sélectionnez un élément dans la liste **méthodes** , puis cliquez sur le bouton **atteindre la définition** .

## <a name="see-also"></a>Voir aussi

[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)
