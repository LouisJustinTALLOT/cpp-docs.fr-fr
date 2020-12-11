---
description: 'En savoir plus sur : paramètres de l’application, Assistant Projet ATL'
title: Paramètres de l’application, Assistant Projet ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.atl.com.appset
helpviewer_keywords:
- ATL Project Wizard, application settings
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
ms.openlocfilehash: 7805fcb8760035ac232a36a42a1cf34273ee42a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158943"
---
# <a name="application-settings-atl-project-wizard"></a>Paramètres de l’application, Assistant Projet ATL

Utilisez la page Paramètres de l' **application** de l’Assistant Projet ATL pour concevoir et ajouter des fonctionnalités de base à un nouveau projet ATL.

## <a name="server-type"></a>Type de serveur

Choisissez l’un des trois types de serveurs :

- **Bibliothèque de liens dynamiques (DLL)**

   Sélectionnez cette option pour créer un serveur in-process.

- **Exécutable (EXE)**

   Sélectionnez cette option pour créer un serveur hors processus local. Cette option n’autorise pas la prise en charge de MFC ou COM+ 1,0. Elle n’autorise pas la fusion du code proxy/stub.

- **Service (EXE)**

   Sélectionnez cette option pour créer une application Windows qui s’exécute en arrière-plan au démarrage de Windows. Cette option n’autorise pas la prise en charge de MFC ou COM+ 1,0 ou n’autorise pas la fusion du code proxy/stub.

## <a name="additional-options"></a>Options supplémentaires

> [!NOTE]
> Toutes les options supplémentaires sont disponibles uniquement pour les projets DLL.

- **Autoriser la fusion du code proxy/stub**

   Activez la case à cocher **autoriser la fusion du code proxy/stub** pour des raisons pratiques lorsque des interfaces de marshaling sont requises. Cette option place le proxy généré par MIDL et le code stub dans le même exécutable que le serveur.

- **Prise en charge MFC**

   Sélectionnez cette option pour spécifier que votre objet comprend la prise en charge MFC. Cette option lie votre projet aux bibliothèques MFC afin que vous puissiez accéder à toutes les classes et fonctions qu’ils contiennent.

- **Prise en charge de COM+ 1,0**

   Sélectionnez cette option pour modifier les paramètres de génération du projet afin de prendre en charge les composants COM+ 1,0. En plus de la liste standard des bibliothèques, l’Assistant ajoute la bibliothèque spécifique au composant COM+ 1,0. lib

   En outre, le mtxex.dll est différé sur le système hôte lorsque votre application est lancée.

- **Inscription du composant de support**

   Si votre projet ATL contient la prise en charge des composants COM+ 1,0, vous pouvez définir cette option. L’inscription de composants permet à votre objet COM+ 1,0 d’obtenir une liste de composants, d’inscrire des composants ou d’annuler l’inscription de composants (individuellement ou en une seule fois).

## <a name="see-also"></a>Voir aussi

[Assistant Projet ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)
