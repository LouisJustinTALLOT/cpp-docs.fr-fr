---
title: Assistant classe MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.wizards.classwizard
dev_langs:
- C++
helpviewer_keywords:
- wizards (MFC)
- MFC Class Wizard
ms.assetid: 8b0dd867-5d07-4214-99be-2a1c1995e6d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31e8b6064b9e81edac1c7f4c8aac8e20f1f72296
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438455"
---
# <a name="mfc-class-wizard"></a>Classe MFC (Assistant)

Vous permet d’ajouter des messages et des gestionnaires de messages aux classes dans votre projet. Vous pouvez également démarrer d’autres Assistants ou ajouter une classe à votre projet.

Pour ouvrir le **Assistant classe MFC**, dans le **projet** menu, cliquez sur **Assistant classe**. Pour ouvrir l’Assistant avec un raccourci clavier, tapez CTRL + MAJ + X.

## <a name="uielement-list"></a>Liste des éléments d’interface

- **Projet**

   Le nom d’un projet dans votre solution.

   Vous pouvez sélectionner d’autres projets dans votre solution dans la zone de liste déroulante.

- **Nom de classe**

   Le nom d’une classe dans votre projet.

   Lorsque vous sélectionnez une classe dans le **nom de la classe** liste, les données de la classe remplissent les contrôles dans le **Assistant classe MFC**. Lorsque vous modifiez la valeur d’un contrôle, les données dans la classe sélectionnée sont affectées.

- **Ajouter une classe**

   Permet d’ajouter une classe à partir de plusieurs sources.

   Selon votre sélection, le **Assistant Ajouter une classe MFC**, **Assistant Ajouter une classe à partir d’une Typelib**, **Assistant Ajout d’une classe à partir d’un contrôle ActiveX**, ou **ODBC MFC Assistant consommateur** est démarré.

- **Classe de base**

   La classe de base de la classe qui s’affiche dans **nom de la classe**.

- **Déclaration de classe**

   La classe dans laquelle le **nom de la classe** classe est déclarée.

   Le **déclaration de classe** zone s’affiche uniquement si le nom est différent du nom dans **implémentation de la classe**.

- **Ressources**

   L’ID de la ressource dans **nom de la classe**, le cas échéant. Sinon, le **ressource** zone est vide.

- **Implémentation de la classe**

   Le nom du fichier qui contient l’implémentation de la classe dans **nom de la classe**.

   Vous pouvez sélectionner un fichier d’implémentation différentes en cliquant sur la flèche. Le tableau suivant répertorie les options disponibles.

   |Option|Description|
   |------------|-----------------|
   |**Ouvrir un fichier**|Quitte l’Assistant de classe et ouvre le fichier d’implémentation de classe actuel.|
   |**Ouvrir le dossier contenant**|Ouvre le dossier qui contient le fichier d’implémentation de classe actuel.|
   |**Copier le chemin complet dans le Presse-papiers**|Copie le chemin d’accès du fichier d’implémentation en cours dans le Presse-papiers.|

- **Commandes**

   Vous permet d’ajouter, supprimer, modifier ou recherchez une commande et son gestionnaire de messages.

   Pour ajouter un gestionnaire, cliquez sur **ajouter un gestionnaire**, ou double-cliquez sur un élément dans le **ID d’objet** liste ou **Messages** liste. Le nom de la fonction, l’ID et le message résultant sont affichés dans le **fonctions membres** liste.

   Pour supprimer un gestionnaire, sélectionnez un élément dans le **fonctions membres** liste, puis cliquez sur **supprimer le gestionnaire**.

   Pour modifier un gestionnaire, double-cliquez sur l’élément correspondant dans le **fonctions membres** liste. Ou sélectionnez un élément dans la zone de liste, puis cliquez **modifier le Code**.

- **Messages**

   Vous permet d’ajouter, supprimer, modifier ou recherchez un message et son gestionnaire de messages.

   Pour ajouter un gestionnaire, cliquez sur **ajouter un gestionnaire**, ou double-cliquez sur un élément dans le **Messages** liste.

   Pour ajouter un message personnalisé, cliquez sur **ajouter un Message personnalisé** ou appuyez sur la touche entrée, puis spécifiez les valeurs dans le **ajouter un Message personnalisé** boîte de dialogue. Dans cette boîte de dialogue, vous pouvez également sélectionner **Message inscrit** pour gérer un message de fenêtre est garanti être unique dans tout le système d’exploitation.

- **Fonctions virtuelles**

   Vous permet d’ajouter, supprimer, modifier ou recherchez une fonction virtuelle, ou une fonction virtuelle substituée.

- **Variables membres**

   Vous permet d’ajouter, supprimer, modifier ou rechercher une variable membre.

- **Méthodes**

   Permet d’ajouter, supprimer, ou rechercher une méthode et également accéder à la définition ou déclaration d’une méthode.

   Pour ajouter une méthode, cliquez sur **ajouter une méthode**, puis spécifiez les valeurs dans le **ajouter une méthode** boîte de dialogue.

   Pour supprimer une méthode, sélectionnez un élément dans le **méthodes** liste, puis cliquez sur **méthode Delete**.

   Pour afficher une déclaration, sélectionnez un élément dans le **méthodes** liste, puis cliquez sur **atteindre la déclaration.**

   Pour afficher une définition, double-cliquez sur un élément dans le **méthodes** liste. Ou sélectionnez un élément dans le **méthodes** liste, puis cliquez sur le **atteindre la définition** bouton.

## <a name="see-also"></a>Voir aussi

[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)
