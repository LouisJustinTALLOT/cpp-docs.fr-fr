---
title: Créer des CC++ /dll dans Visual Studio
description: Vue d’ensemble de la raison et de la manière de créer C++ et d’utiliser des dll avec dans Visual Studio.
ms.date: 01/27/2020
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 7083924f137fa9283da40404c7d15183e59c0b1c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417354"
---
# <a name="create-cc-dlls-in-visual-studio"></a>Créer des CC++ /dll dans Visual Studio

Dans Windows, une bibliothèque de liens dynamiques (DLL) est un type de fichier exécutable qui agit comme une bibliothèque partagée de fonctions et de ressources. La liaison dynamique est une fonctionnalité du système d’exploitation. Il permet à un exécutable d’appeler des fonctions ou d’utiliser des ressources stockées dans un fichier séparé. Ces fonctions et ressources peuvent être compilées et déployées séparément des exécutables qui les utilisent.

Une DLL n’est pas un exécutable autonome. Les dll s’exécutent dans le contexte des applications qui les appellent. Le système d’exploitation charge la DLL dans l’espace mémoire d’une application. Elle est effectuée lorsque l’application est chargée (*liaison implicite*) ou à la demande au moment de l’exécution (*liaison explicite*). Les DLL facilitent également le partage des fonctions et des ressources entre les fichiers exécutables. Plusieurs applications peuvent accéder simultanément au contenu d'une copie de la DLL en mémoire.

## <a name="differences-between-dynamic-linking-and-static-linking"></a>Différences entre la liaison dynamique et la liaison statique

La liaison statique copie tout le code d’objet d’une bibliothèque statique dans les exécutables qui l’utilisent lors de leur génération. La liaison dynamique inclut uniquement les informations requises par Windows au moment de l’exécution pour rechercher et charger la DLL qui contient un élément de données ou une fonction. Lorsque vous créez une DLL, vous créez également une bibliothèque d’importation qui contient ces informations. Quand vous générez un exécutable qui appelle la DLL, l’éditeur de liens utilise les symboles exportés dans la bibliothèque d’importation pour stocker ces informations pour le chargeur Windows. Lorsque le chargeur charge une DLL, la DLL est mappée dans l’espace mémoire de votre application. Si elle est présente, une fonction spéciale dans la DLL, `DllMain`, est appelée pour effectuer toute initialisation requise par la DLL.

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>Différences entre les applications et les dll

Même si les dll et les applications sont tous deux des modules exécutables, ils diffèrent de plusieurs façons. La différence la plus évidente est que vous ne pouvez pas exécuter une DLL. Du point de vue du système, il existe deux différences fondamentales entre les applications et les dll :

- Une application peut avoir plusieurs instances d’elle-même s’exécutant simultanément dans le système. Une DLL ne peut avoir qu’une seule instance.

- Une application peut être chargée en tant que processus. Il peut posséder des éléments tels qu’une pile, des threads d’exécution, de la mémoire globale, des handles de fichiers et une file d’attente de messages. Une DLL ne peut pas être propriétaire de ces éléments.

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Avantages de l’utilisation des dll

La liaison dynamique au code et aux ressources offre plusieurs avantages par rapport à la liaison statique :

- La liaison dynamique économise de la mémoire et réduit les échanges. De nombreux processus peuvent utiliser une DLL simultanément, en partageant une seule copie des parties en lecture seule d’une DLL en mémoire. En revanche, chaque application générée à l’aide d’une bibliothèque liée de manière statique dispose d’une copie complète du code de bibliothèque que Windows doit charger en mémoire.

- La liaison dynamique économise de l’espace disque et de la bande passante. De nombreuses applications peuvent partager une seule copie de la DLL sur le disque. En revanche, chaque application générée à l’aide d’une bibliothèque de liens statiques a le code de bibliothèque lié à son image exécutable. Qui utilise plus d’espace disque et prend plus de bande passante pour le transfert.

- La maintenance, les correctifs de sécurité et les mises à niveau peuvent être plus simples. Quand vos applications utilisent des fonctions courantes dans une DLL, vous pouvez implémenter des correctifs de bogues et déployer des mises à jour dans la DLL. Lorsque les dll sont mises à jour, les applications qui les utilisent n’ont pas besoin d’être recompilées ou reliées. Ils peuvent utiliser la nouvelle DLL dès qu’elle est déployée. En revanche, lorsque vous effectuez des corrections dans du code objet lié de manière statique, vous devez recréer un lien et redéployer chaque application qui l’utilise.

- Vous pouvez utiliser des dll pour fournir un support après le marché. Par exemple, une DLL de pilote d’affichage peut être modifiée pour prendre en charge un affichage qui n’était pas disponible lors de l’envoi de l’application.

- Vous pouvez utiliser la liaison explicite pour découvrir et charger des dll au moment de l’exécution. Par exemple, les extensions d’application qui ajoutent de nouvelles fonctionnalités à votre application sans la reconstruire ou la redéployer.

- La liaison dynamique facilite la prise en charge d’applications écrites dans des langages de programmation différents. Les programmes écrits dans différents langages de programmation peuvent appeler la même fonction DLL à condition que les programmes suivent la Convention d’appel de la fonction. Les programmes et la fonction DLL doivent être compatibles des manières suivantes : l’ordre dans lequel la fonction attend que ses arguments fassent l’objet d’un push sur la pile. Si la fonction ou l’application est responsable du nettoyage de la pile. Et, si des arguments sont passés dans les registres.

- La liaison dynamique fournit un mécanisme permettant d’étendre les classes de la bibliothèque MFC (Microsoft Foundation Class Library). Vous pouvez dériver des classes des classes MFC existantes et les placer dans une DLL d’extension MFC pour une utilisation par les applications MFC.

- La liaison dynamique rend la création de versions internationales de votre application plus facile. Les dll sont un moyen pratique de fournir des ressources spécifiques aux paramètres régionaux, ce qui facilite grandement la création de versions internationales d’une application. Au lieu d’expédier de nombreuses versions localisées de votre application, vous pouvez placer les chaînes et les images de chaque langage dans une DLL de ressource distincte. Ensuite, votre application peut charger les ressources appropriées pour ces paramètres régionaux au moment de l’exécution.

Un inconvénient potentiel de l’utilisation des dll est que l’application n’est pas autonome. Cela dépend de l’existence d’un module DLL distinct : vous devez le déployer ou le vérifier dans le cadre de votre installation.

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Plus d’informations sur la façon de créer et d’utiliser des dll

Les articles suivants fournissent des informations détaillées sur la création de CC++ /dll dans Visual Studio.

[Procédure pas à pas : création et utilisation d’uneC++bibliothèque de liens dynamiques ()](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)\
Montre comment créer et utiliser une DLL à l'aide de Visual Studio.

[Types de dll](kinds-of-dlls.md)\
Fournit des informations sur les différentes sortes de DLL qui peuvent être générées.

Forum [aux questions](dll-frequently-asked-questions.md) sur les dll\
Fournit des réponses à des questions fréquentes concernant les DLL.

[Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md)\
Décrit la liaison explicite et implicite à une DLL.

[Initialiser une DLL](run-time-library-behavior.md#initializing-a-dll)\
Traite du code d’initialisation de la DLL qui doit s’exécuter lors du chargement de votre DLL.

[Dll et comportement C++ de la bibliothèque Runtime visuelle](run-time-library-behavior.md)\
Décrit la séquence de démarrage de la DLL de la bibliothèque Runtime.

[LoadLibrary et AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)\
Décrit l’utilisation de `LoadLibrary` et `AfxLoadLibrary` pour une liaison explicite à une DLL au moment de l’exécution.

\ [GetProcAddress](getprocaddress.md)
Traite de l’utilisation de `GetProcAddress` pour obtenir l’adresse d’une fonction exportée dans la DLL.

[FreeLibrary et AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)\
Traite de l’utilisation de `FreeLibrary` et `AfxFreeLibrary` lorsque le module DLL n’est plus nécessaire.

\ [de l’ordre de recherche de la bibliothèque de liens dynamiques](/windows/win32/Dlls/dynamic-link-library-search-order)
Décrit le chemin d’accès que le système d’exploitation Windows utilise pour rechercher une DLL sur le système.

[États du module d’une DLL MFC normale liée de manière dynamique aux mfc](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)\
Décrit les États du module d’une DLL MFC normale liée de manière dynamique aux MFC.

[Dll d’extension MFC](extension-dlls-overview.md)\
Décrit les dll qui implémentent généralement des classes réutilisables dérivées des classes MFC existantes.

[Création d’une dll de ressources uniquement](creating-a-resource-only-dll.md)\
Traite des DLL de ressource uniquement, qui ne contiennent que des ressources, telles que des icônes, des images bitmap, des chaînes et des boîtes de dialogue.

[Ressources localisées dans les applications MFC : dll satellites](localized-resources-in-mfc-applications-satellite-dlls.md)\
Fournit une prise en charge améliorée pour les DLL satellites, une fonctionnalité qui vous aide à créer des applications localisées pour différentes langues.

[Importation et exportation de](importing-and-exporting.md)\
Décrit l'importation de symboles publics dans une application ou l'exportation de fonctions à partir d'une DLL.

[Technologie active et dll](active-technology-and-dlls.md)\
Autorise l'implémentation des serveurs d'objets dans une DLL.

[Automatisation dans une DLL](automation-in-a-dll.md)\
Décrit ce que fournit l'option Automation de l'Assistant DLL MFC.

[Conventions d’affectation des noms pour les DLL MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)\
Décrit comment les DLL et les bibliothèques incluses dans les MFC obéissent aux règles d'une convention d'attribution de noms structurée.

[Appel de fonctions dll à partir d’applications Visual Basic](calling-dll-functions-from-visual-basic-applications.md)\
Explique comment appeler des fonctions DLL à partir d'applications Visual Basic.

## <a name="related-sections"></a>Sections connexes

[Utilisation de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)\
Décrit les DLL MFC standard, qui vous permettent d’utiliser la bibliothèque MFC dans le cadre d’une bibliothèque de liens dynamiques Windows.

[Version DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)\
Décrit comment vous pouvez utiliser les bibliothèques de liens dynamiques partagées MFCxx. dll et MFCxxD. dll (où x est le numéro de version MFC) avec les applications MFC et les dll d’extension MFC.
