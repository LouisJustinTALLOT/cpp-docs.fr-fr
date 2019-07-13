---
title: Création du projet (Didacticiel ATL, Partie 1)
ms.custom: get-started-article
ms.date: 05/06/2019
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
ms.openlocfilehash: 0df793b23aaec57835774252eeac21b092f8a9e9
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861022"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Création du projet (Didacticiel ATL, Partie 1)

Ce didacticiel vous guide pas à pas dans un projet ATL sans attributs qui crée un objet ActiveX qui affiche un polygone. L’objet inclut des options permettant à l’utilisateur pour modifier le nombre de côtés qui composent le polygone et le code pour actualiser l’affichage.

> [!NOTE]
> ATL et MFC ne sont généralement pas pris en charge dans les éditions Express de Visual Studio.

> [!NOTE]
> Ce didacticiel crée le même code source que l’exemple de polygone. Si vous souhaitez éviter d’entrer le code source manuellement, vous pouvez le télécharger à partir de la [exemple Polygon](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/Polygon). Vous pouvez alors faire référence au code source de polygone que vous parcourez le didacticiel, ou l’utiliser pour rechercher les erreurs dans votre propre projet.
> Pour compiler, ouvrez stdafx.h et remplacez :
> ```
> #ifndef WINVER
> #define WINVER 0x0400
> #endif
> ```
> par
> ```
> #ifndef WINVER
> #define WINVER 0x0500
> #define _WIN32_WINNT 0x0500
> #endif
> ```
> Le compilateur se plaindra toujours sur `regsvr32` ne ferme ne pas correctement, mais vous devez toujours se trouver la DLL du contrôle générée et peut être utilisé.

### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>Pour créer le projet ATL initial à l’aide de l’Assistant Projet ATL

1. Dans Visual Studio 2017 et versions antérieures : **Fichier** > **nouveau** > **projet**. L’ouverture du **Visual C++**  onglet et sélectionnez **MFC/ATL**. Sélectionnez **projet ATL**.

   Dans Visual Studio 2019 : Choisissez **fichier** > **New** > **projet**, tapez « atl » dans la zone de recherche, choisissez **projet ATL**.

1. Type *polygone* en tant que le nom du projet.

    L’emplacement pour le code source est généralement par défaut \Users\\\<nom d’utilisateur > \source\repos et un nouveau dossier seront créé automatiquement.

1. Dans Visual Studio 2019, acceptez les valeurs par défaut et cliquez sur **OK**. 
   Dans Visual Studio 2017, cliquez sur **OK** pour ouvrir le **projet ATL** Assistant. Cliquez sur **paramètres d’Application** pour afficher les options disponibles. Étant donné que ce projet crée un contrôle et un contrôle doit être un serveur in-process, laisser le **type d’Application** en tant que DLL. Cliquez sur **OK**.

Visual Studio crée le projet en générant plusieurs fichiers. Vous pouvez afficher ces fichiers dans **l’Explorateur de solutions** en développant le `Polygon` objet. Les fichiers sont répertoriés ci-dessous.

|Fichier|Description|
|----------|-----------------|
|Polygon.cpp|Contient l’implémentation de `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`, et `DllUnregisterServer`. Contient également le mappage de l’objet, qui est une liste des objets ATL dans votre projet. Cette valeur est initialement vide.|
|Polygon.def|Ce fichier de définition de module fournit l’éditeur de liens avec des informations sur les exportations requises par votre DLL.|
|Polygon.idl|L’interface fichier definition language, qui décrit les interfaces spécifiques à vos objets.|
|Polygon.rgs|Ce script de Registre contient des informations pour l’inscription de DLL de votre programme.|
|Polygon.rc|Le fichier de ressources, qui contient initialement les informations de version et une chaîne contenant le nom du projet.|
|Resource.h|Fichier d’en-tête pour le fichier de ressources.|
|Polygonps.def|Ce fichier de définition de module fournit l’éditeur de liens avec des informations sur les exportations requises par le code proxy et le stub qui prennent en charge les appels entre les cloisonnements.|
|stdafx.cpp|Le fichier sera `#include` les fichiers d’implémentation ATL.|
|stdafx.h|Le fichier sera `#include` les fichiers d’en-tête ATL.|

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet `Polygon`.

1. Dans le menu contextuel, cliquez sur **propriétés**.

1. Cliquez sur **l’éditeur de liens**. Modifier le **par UserRedirection** option **Oui**.

1. Cliquez sur **OK**.

Dans l’étape suivante, vous allez ajouter un contrôle à votre projet.

[À l’étape 2](../atl/adding-a-control-atl-tutorial-part-2.md)

## <a name="see-also"></a>Voir aussi

[Tutoriel](../atl/active-template-library-atl-tutorial.md)
