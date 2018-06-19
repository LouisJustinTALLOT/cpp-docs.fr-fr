---
title: Création du projet (ATL didacticiel, partie 1) | Documents Microsoft
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1aedf7b4112d4c8d4bb5b2a174e93925f5a46ce5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357716"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Création du projet (Didacticiel ATL, Partie 1)
Ce didacticiel vous guide pas à pas dans un projet ATL sans attributs qui crée un objet ActiveX qui affiche un polygone. L’objet comprend des options permettant à l’utilisateur pour modifier le nombre de côtés qui composent le polygone et le code pour actualiser l’affichage.  
  
> [!NOTE]
>  ATL et MFC ne sont généralement pas prises en charge dans les éditions Express de Visual Studio.  
  
> [!NOTE]
>  Ce didacticiel crée le même code source que l’exemple de polygone. Si vous souhaitez éviter d’entrer le code source manuellement, vous pouvez le télécharger à partir de la [exemple Polygon](../visual-cpp-samples.md). Vous pouvez alors faire référence au code source Polygon que vous parcourez le didacticiel ou l’utilisez pour rechercher les erreurs dans votre propre projet.  
  
### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>Pour créer le projet ATL initial à l’aide de l’Assistant Projet ATL  
  
1.  Dans l’environnement de développement Visual Studio, cliquez sur **nouveau** sur la **fichier** menu, puis sur **projet**.  
  
2.  Cliquez sur le **projets Visual C++** et sélectionnez **projet ATL**.  
  
3.  Type `Polygon` comme nom du projet.  
  
     L’emplacement du code source de généralement par défaut est Mes Documents\Visual Studio projets, et un nouveau dossier sera créé automatiquement.  
  
4.  Cliquez sur **OK** et l’Assistant Projet ATL s’ouvre.  
  
5.  Cliquez sur **paramètres de l’Application** pour afficher les options disponibles.  
  
6.  Lorsque vous créez un contrôle, et un contrôle doit être un serveur in-process, laissez le **type d’Application** en tant que DLL.  
  
7.  Conservez les autres options de leurs valeurs par défaut, puis cliquez sur **Terminer**.  
  
 L’Assistant Projet ATL créera le projet en générant plusieurs fichiers. Vous pouvez afficher ces fichiers dans l’Explorateur de solutions, développez l’objet de polygone. Les fichiers sont répertoriés ci-dessous.  
  
|Fichier|Description|  
|----------|-----------------|  
|Polygon.cpp|Contient l’implémentation de `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`, et `DllUnregisterServer`. Contient également le mappage de l’objet, qui est une liste des objets dans votre projet ATL. Cette valeur est initialement vide.|  
|Polygon.def|Ce fichier de définition de module fournit l’éditeur de liens avec des informations sur les exportations requises par votre DLL.|  
|Polygon.idl|L’interface fichier definition language, qui décrit les interfaces spécifiques à vos objets.|  
|Polygon.rgs|Ce script de Registre contient des informations pour l’inscription des DLL de votre programme.|  
|Polygon.rc|Le fichier de ressources, qui contient initialement les informations de version et une chaîne contenant le nom du projet.|  
|Resource.h|Le fichier d’en-tête pour le fichier de ressources.|  
|Polygonps.def|Ce fichier de définition de module fournit à l’éditeur de liens avec des informations sur les exportations requises par le code proxy et le stub qui prennent en charge les appels entre les cloisonnements.|  
|stdafx.cpp|Le fichier sera `#include` les fichiers d’implémentation ATL.|  
|stdafx.h|Le fichier sera `#include` les fichiers d’en-tête ATL.|  
  
1.  Dans l’Explorateur de solutions, cliquez sur le `Polygon` projet.  
  
2.  Dans le menu contextuel, cliquez sur **propriétés**.  
  
3.  Cliquez sur **l’éditeur de liens**. Modifier la **par UserRedirection** option **Oui**.  
  
4.  Cliquez sur **OK**.  
  
 Dans l’étape suivante, vous allez ajouter un contrôle à votre projet.  
  
 [À l’étape 2](../atl/adding-a-control-atl-tutorial-part-2.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel](../atl/active-template-library-atl-tutorial.md)

