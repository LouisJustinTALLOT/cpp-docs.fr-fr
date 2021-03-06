---
description: 'En savoir plus sur : création du projet (Didacticiel ATL, partie 1)'
title: Création du projet (Didacticiel ATL, Partie 1)
ms.custom: get-started-article
ms.date: 08/19/2019
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
ms.openlocfilehash: f594294b5d97222791a3f3f43c147fae9514889b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148083"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Création du projet (Didacticiel ATL, Partie 1)

Ce didacticiel vous guide pas à pas dans un projet ATL sans attributs qui crée un objet ActiveX qui affiche un polygone. L’objet comprend des options permettant à l’utilisateur de modifier le nombre de côtés composant le polygone et le code d’actualiser l’affichage.

> [!NOTE]
> Ce didacticiel crée le même code source que l’exemple Polygon. Si vous souhaitez éviter d’entrer le code source manuellement, vous pouvez le télécharger à partir de l' [exemple de résumé de polygone](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/Polygon). Vous pouvez ensuite faire référence au code source Polygon au fur et à mesure que vous parcourez le didacticiel, ou l’utiliser pour rechercher les erreurs dans votre propre projet.
> Pour compiler, ouvrez *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures) et remplacez :
>
> ```
> #ifndef WINVER
> #define WINVER 0x0400
> #endif
> ```
>
> par
>
> ```
> #ifndef WINVER
> #define WINVER 0x0500
> #define _WIN32_WINNT 0x0500
> #endif
> ```
>
> Le compilateur se plaint toujours de `regsvr32` ne pas quitter correctement, mais la dll du contrôle doit toujours être générée et utilisable.

### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>Pour créer le projet ATL initial à l’aide de l’Assistant Projet ATL

1. Dans Visual Studio 2017 et versions antérieures : **fichier**  >  **nouveau**  >  **projet**. Ouvrez l’onglet **Visual C++** et sélectionnez **MFC/ATL**. Sélectionnez **projet ATL**.

   Dans Visual Studio 2019 : choisissez **fichier**  >  **nouveau**  >  **projet**, tapez « ATL » dans la zone de recherche, puis choisissez **projet ATL**.

1. Tapez *Polygon* comme nom de projet.

    L’emplacement du code source est généralement défini par défaut sur \Utilisateurs \\ \<username> \source\repos, et un nouveau dossier est créé automatiquement.

1. Dans Visual Studio 2019, acceptez les valeurs par défaut et cliquez sur **OK**.
   Dans Visual Studio 2017, cliquez sur **OK** pour ouvrir l’Assistant **projet ATL** . Cliquez sur paramètres de l' **application** pour afficher les options disponibles. Étant donné que ce projet crée un contrôle et qu’un contrôle doit être un serveur in-process, laissez le **type d’application** en tant que dll. Cliquez sur **OK**.

Visual Studio crée le projet en générant plusieurs fichiers. Vous pouvez afficher ces fichiers dans **Explorateur de solutions** en développant l' `Polygon` objet. Les fichiers sont répertoriés ci-dessous.

::: moniker range="<=msvc-150"

|Fichier|Description|
|----------|-----------------|
|Polygon. cpp|Contient l’implémentation de `DllMain` , `DllCanUnloadNow` , `DllGetClassObject` , `DllRegisterServer` et `DllUnregisterServer` . Contient également le mappage d’objet, qui est une liste des objets ATL dans votre projet. Ce champ est initialement vide.|
|Polygon. def|Ce fichier de définition de module fournit à l’éditeur de liens des informations sur les exportations requises par votre DLL.|
|Polygon. idl|Le fichier du langage de définition d’interface, qui décrit les interfaces spécifiques à vos objets.|
|Polygon. RGS|Ce script de registre contient des informations sur l’inscription de la DLL de votre programme.|
|Polygon. RC|Fichier de ressources, qui contient initialement les informations de version et une chaîne contenant le nom du projet.|
|Resource.h|Fichier d’en-tête pour le fichier de ressources.|
|Polygonps. def|Ce fichier de définition de module fournit à l’éditeur de liens des informations sur les exportations requises par le proxy et le code stub qui prennent en charge les appels entre les cloisonnements.|
|stdafx.cpp|Fichier qui sera `#include` *stdafx. h*.|
|stdafx.h|Fichier qui va `#include` précompiler et précompiler les fichiers d’en-tête ATL.|

::: moniker-end

::: moniker range=">=msvc-160"

|Fichier|Description|
|----------|-----------------|
|Polygon. cpp|Contient l’implémentation de `DllMain` , `DllCanUnloadNow` , `DllGetClassObject` , `DllRegisterServer` et `DllUnregisterServer` . Contient également le mappage d’objet, qui est une liste des objets ATL dans votre projet. Ce champ est initialement vide.|
|Polygon. def|Ce fichier de définition de module fournit à l’éditeur de liens des informations sur les exportations requises par votre DLL.|
|Polygon. idl|Le fichier du langage de définition d’interface, qui décrit les interfaces spécifiques à vos objets.|
|Polygon. RGS|Ce script de registre contient des informations sur l’inscription de la DLL de votre programme.|
|Polygon. RC|Fichier de ressources, qui contient initialement les informations de version et une chaîne contenant le nom du projet.|
|Resource.h|Fichier d’en-tête pour le fichier de ressources.|
|Polygonps. def|Ce fichier de définition de module fournit à l’éditeur de liens des informations sur les exportations requises par le proxy et le code stub qui prennent en charge les appels entre les cloisonnements.|
|pch. cpp|Fichier qui sera `#include` *pch. h*.|
|pch. h|Fichier qui va `#include` précompiler et précompiler les fichiers d’en-tête ATL.|

::: moniker-end

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le `Polygon` projet.

1. Dans le menu contextuel, cliquez sur **Propriétés**.

1. Cliquez sur l' **éditeur de liens**. Remplacez l’option **per-UserRedirection par** **Oui**.

1. Cliquez sur **OK**.

À l’étape suivante, vous allez ajouter un contrôle à votre projet.

[À l’étape 2](../atl/adding-a-control-atl-tutorial-part-2.md)

## <a name="see-also"></a>Voir aussi

[Didacticiel](../atl/active-template-library-atl-tutorial.md)
