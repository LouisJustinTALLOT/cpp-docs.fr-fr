---
title: Assistant projet de paramètres d’application, ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.atl.com.appset
dev_langs:
- C++
helpviewer_keywords:
- ATL Project Wizard, application settings
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47fbf95451834e5f8c41e8b6d7e5af7a9746bb85
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357403"
---
# <a name="application-settings-atl-project-wizard"></a>Paramètres de l’application, Assistant Projet ATL
Utilisez le **paramètres de l’Application** page de l’Assistant Projet ATL pour concevoir et ajouter des fonctionnalités de base pour un nouveau projet ATL.  
  
## <a name="server-type"></a>Type de serveur  
 Choisissez une des trois types de serveur :  
  
 **bibliothèque de liens dynamiques (DLL)**  
 Sélectionnez cette option pour créer un serveur in-process.  
  
 **Fichier exécutable (EXE)**  
 Sélectionnez cette option pour créer un serveur out-of-process local. Cette option ne permet pas de prise en charge de MFC ou COM + 1.0. Il n’autorise pas la fusion du code proxy/stub.  
  
 **Service (EXE)**  
 Sélectionnez cette option pour créer une application Windows qui s’exécute en arrière-plan au démarrage de Windows. Cette option ne permet pas de prise en charge de MFC ou COM + 1.0, ou n’autorise pas la fusion du code proxy/stub.  
  
## <a name="additional-options"></a>Options supplémentaires  
  
> [!NOTE]
>  Toutes les options supplémentaires sont disponibles pour les projets DLL.  
  
 **Permettre la fusion du code proxy/stub**  
 Sélectionnez le **permettre la fusion du code proxy/stub** case à cocher pour des raisons pratiques lorsque le marshaling des interfaces est requis. Cette option place le code proxy et stub généré par MIDL dans le même exécutable en tant que le serveur.  
  
 **Prise en charge MFC**  
 Sélectionnez cette option pour spécifier que votre objet inclut la prise en charge MFC. Cette option lie votre projet pour les bibliothèques MFC afin que vous pouvez accéder à toutes les classes et les fonctions qu’ils contiennent.  
  
 **Prise en charge COM + 1.0**  
 Sélectionnez cette option pour modifier les paramètres de génération de projet pour prendre en charge les composants COM + 1.0. En plus de la liste des bibliothèques standard, l’Assistant ajoute le comsvcs.lib spécifique au composant bibliothèque COM + 1.0  
  
 En outre, le mtxex.dll est délai chargé sur le système hôte lorsque votre application est lancée.  
  
-   **Prend en charge l’inscription de composants** si votre projet ATL contient la prise en charge des composants COM + 1.0, vous pouvez définir cette option. L’inscription de composants permet à votre objet COM + 1.0 obtenir une liste des composants, d’inscrire des composants ou d’annuler l’inscription de composants (individuellement ou tous en même temps).  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Projet ATL](../../atl/reference/atl-project-wizard.md)   
 [Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)   
 [Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)

