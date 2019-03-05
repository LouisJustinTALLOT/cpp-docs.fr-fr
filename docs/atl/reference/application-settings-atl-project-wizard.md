---
title: Paramètres de l’application, Assistant Projet ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.atl.com.appset
helpviewer_keywords:
- ATL Project Wizard, application settings
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
ms.openlocfilehash: bd9d5c6ef1ccb86f2968b1e2d2706092b6db45e9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271812"
---
# <a name="application-settings-atl-project-wizard"></a>Paramètres de l’application, Assistant Projet ATL

Utilisez le **paramètres d’Application** page de l’Assistant Projet ATL pour concevoir et ajouter des fonctionnalités de base à un nouveau projet ATL.

## <a name="server-type"></a>Type de serveur

Choisissez une des trois types de serveur :

- **Bibliothèque de liens dynamiques (DLL)**

   Sélectionnez cette option pour créer un serveur in-process.

- **Fichier exécutable (EXE)**

   Sélectionnez cette option pour créer un serveur out-of-process local. Cette option ne permet pas de prise en charge de MFC ou COM + 1.0. Il n’autorise pas la fusion du code proxy/stub.

- **Service (EXE)**

   Sélectionnez cette option pour créer une application Windows qui s’exécute en arrière-plan au démarrage de Windows. Cette option ne permet pas de prise en charge de MFC ou COM + 1.0 ou n’autorise pas la fusion du code proxy/stub.

## <a name="additional-options"></a>Options supplémentaires

> [!NOTE]
> Toutes les options supplémentaires sont disponibles pour les projets DLL.

- **Autoriser la fusion du code proxy/stub**

   Sélectionnez le **autoriser la fusion du code proxy/stub** case à cocher pour des raisons pratiques quand il est nécessaire de marshaling d’interfaces. Cette option place le code proxy et stub généré par MIDL dans le même exécutable en tant que le serveur.

- **Prise en charge MFC**

   Sélectionnez cette option pour spécifier que votre objet inclut la prise en charge MFC. Cette option lie votre projet aux bibliothèques MFC afin que vous pouvez accéder à toutes les classes et les fonctions qu’ils contiennent.

- **Prise en charge COM + 1.0**

   Sélectionnez cette option pour modifier les paramètres de génération de projet pour prendre en charge les composants COM + 1.0. Outre la liste standard des bibliothèques, l’Assistant ajoute le comsvcs.lib spécifique au composant bibliothèque COM + 1.0

   En outre, le mtxex.dll est chargé sur le système hôte lorsque votre application est lancée de délai.

- **Inscription de composants de prise en charge**

   Si votre projet ATL prise en charge des composants COM + 1.0, vous pouvez définir cette option. L’inscription de composants permet à votre objet COM + 1.0 obtenir une liste des composants, d’inscrire des composants ou d’annuler l’inscription de composants (individuellement ou tous en même temps).

## <a name="see-also"></a>Voir aussi

[Assistant Projet ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)
