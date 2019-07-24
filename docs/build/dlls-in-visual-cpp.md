---
title: Créer des CC++ /dll dans Visual Studio
ms.date: 07/18/2019
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 9f5b34fda8a429f8e55631e1e0125ed6f79d5bae
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341071"
---
# <a name="create-cc-dlls-in-visual-studio"></a>Créer des CC++ /dll dans Visual Studio

Dans Windows, une bibliothèque de liens dynamiques (DLL) est un type de fichier exécutable qui agit comme une bibliothèque partagée de fonctions et de ressources. La liaison dynamique est une fonctionnalité du système d’exploitation qui permet à un exécutable d’appeler des fonctions ou d’utiliser des ressources stockées dans un fichier séparé. Ces fonctions et ressources peuvent être compilées et déployées séparément des exécutables qui les utilisent. Une DLL n’est pas un exécutable autonome; Il s’exécute dans le contexte d’une application qui l’appelle. Le système d’exploitation peut charger la DLL dans l’espace mémoire d’une application lorsque celle-ci est chargée (*liaison implicite*) ou à la demande au moment de l’exécution (*liaison explicite*). Les DLL facilitent également le partage des fonctions et des ressources entre les fichiers exécutables. Plusieurs applications peuvent accéder simultanément au contenu d'une copie de la DLL en mémoire.

## <a name="differences-between-dynamic-linking-and-static-linking"></a>Différences entre la liaison dynamique et la liaison statique

La liaison statique copie tout le code d’objet d’une bibliothèque statique dans les exécutables qui l’utilisent lorsqu’ils sont générés. La liaison dynamique inclut uniquement les informations requises par Windows au moment de l’exécution pour rechercher et charger la DLL qui contient un élément de données ou une fonction. Lorsque vous créez une DLL, vous créez également une bibliothèque d’importation qui contient ces informations. Quand vous générez un exécutable qui appelle la DLL, l’éditeur de liens utilise les symboles exportés dans la bibliothèque d’importation pour stocker ces informations pour le chargeur Windows. Lorsque le chargeur charge une DLL, la DLL est mappée dans l’espace mémoire de votre application. Si elle est présente, une fonction spéciale dans la `DllMain`dll,, est appelée pour effectuer toute initialisation requise par la dll.

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>Différences entre les applications et les dll

Même si les dll et les applications sont tous deux des modules exécutables, ils diffèrent de plusieurs façons. Pour l’utilisateur final, la différence la plus évidente est que les dll ne sont pas des applications qui peuvent être exécutées directement. Du point de vue du système, il existe deux différences fondamentales entre les applications et les dll:

- Une application peut avoir plusieurs instances d’elle-même s’exécutant simultanément dans le système, alors qu’une DLL ne peut avoir qu’une seule instance.

- Une application peut être chargée en tant que processus qui peut posséder des éléments tels qu’une pile, des threads d’exécution, de la mémoire globale, des handles de fichiers et une file d’attente de messages, mais pas une DLL.

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Avantages de l’utilisation des dll

La liaison dynamique au code et aux ressources offre plusieurs avantages par rapport à la liaison statique:

- La liaison dynamique économise de la mémoire et réduit les échanges. De nombreux processus peuvent utiliser une DLL simultanément, en partageant une seule copie des parties en lecture seule d’une DLL en mémoire. En revanche, chaque application générée à l’aide d’une bibliothèque liée de manière statique dispose d’une copie complète du code de bibliothèque que Windows doit charger en mémoire.

- La liaison dynamique économise de l’espace disque et de la bande passante. De nombreuses applications peuvent partager une seule copie de la DLL sur le disque. En revanche, chaque application générée à l’aide d’une bibliothèque de liens statiques a le code de bibliothèque lié à son image exécutable, qui utilise plus d’espace disque et prend plus de bande passante pour le transfert.

- La maintenance, les correctifs de sécurité et les mises à niveau peuvent être plus simples. Lorsque vos applications utilisent des fonctions courantes dans une DLL, tant que les arguments de fonction et les valeurs de retour ne changent pas, vous pouvez implémenter des correctifs de bogues et déployer des mises à jour dans la DLL. Lorsque les dll sont mises à jour, les applications qui les utilisent n’ont pas besoin d’être recompilées ou reliées, et elles utilisent la nouvelle DLL dès qu’elles sont déployées. En revanche, les correctifs que vous apportez dans le code objet lié statiquement nécessitent que vous reliez et redéployez chaque application qui l’utilise.

- Vous pouvez utiliser des dll pour fournir un support après le marché. Par exemple, une DLL de pilote d’affichage peut être modifiée pour prendre en charge un affichage qui n’était pas disponible lors de l’envoi de l’application.

- Vous pouvez utiliser la liaison explicite pour découvrir et charger des dll au moment de l’exécution, telles que des extensions d’application qui ajoutent de nouvelles fonctionnalités à votre application sans la reconstruire ou la redéployer.

- La liaison dynamique facilite la prise en charge d’applications écrites dans des langages de programmation différents. Les programmes écrits dans différents langages de programmation peuvent appeler la même fonction DLL à condition que les programmes suivent la Convention d’appel de la fonction. Les programmes et la fonction DLL doivent être compatibles des manières suivantes: l’ordre dans lequel la fonction attend que ses arguments fassent l’objet d’un push sur la pile, si la fonction ou l’application est responsable du nettoyage de la pile et si des arguments sont passé dans les registres.

- La liaison dynamique fournit un mécanisme permettant d’étendre les classes de la bibliothèque MFC. Vous pouvez dériver des classes des classes MFC existantes et les placer dans une DLL d’extension MFC pour une utilisation par les applications MFC.

- La liaison dynamique rend la création de versions internationales de votre application plus facile. Les dll sont un moyen pratique de fournir des ressources spécifiques aux paramètres régionaux, ce qui facilite grandement la création de versions internationales d’une application. Au lieu d’expédier de nombreuses versions localisées de votre application, vous pouvez placer les chaînes et les images de chaque langage dans une DLL de ressource distincte, puis votre application peut charger les ressources appropriées pour ces paramètres régionaux au moment de l’exécution.

Un inconvénient potentiel de l’utilisation des dll est que l’application n’est pas autonome; Cela dépend de l’existence d’un module DLL distinct que vous devez déployer ou vérifier vous-même dans le cadre de votre installation.

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Plus d’informations sur la façon de créer et d’utiliser des dll

Les rubriques suivantes fournissent des informations détaillées sur la création de CC++ /dll dans Visual Studio.

[Procédure pas à pas : création et utilisation d’une bibliothèque de liens dynamiques (C++)](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
Montre comment créer et utiliser une DLL à l'aide de Visual Studio.

[Genres de DLL](kinds-of-dlls.md)<br/>
Fournit des informations sur les différentes sortes de DLL qui peuvent être générées.

[Forum aux questions sur les DLL](dll-frequently-asked-questions.md)<br/>
Fournit des réponses à des questions fréquentes concernant les DLL.

[Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md)<br/>
Décrit la liaison explicite et implicite à une DLL.

[Initialiser une DLL](run-time-library-behavior.md#initializing-a-dll)<br/>
Traite du code d’initialisation de la DLL qui doit s’exécuter lors du chargement de votre DLL.

[DLL et comportement de la bibliothèque runtime Visual C++](run-time-library-behavior.md)<br/>
Décrit comment la bibliothèque Runtime exécute la séquence de démarrage de la DLL.

[LoadLibrary et AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)<br/>
Traite de l'  utilisation de `AfxLoadLibrary` LoadLibrary et de pour établir une liaison explicite à une dll au moment de l’exécution.

[GetProcAddress](getprocaddress.md)<br/>
Décrit l’utilisation de **GetProcAddress** pour obtenir l’adresse d’une fonction exportée dans la dll.

[FreeLibrary et AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)<br/>
Traite de l'  utilisation de `AfxFreeLibrary` FreeLibrary et de lorsque le module dll n’est plus nécessaire.

[Ordre de recherche de la bibliothèque de liens dynamiques](/windows/desktop/Dlls/dynamic-link-library-search-order)<br/>
Décrit le chemin d’accès que le système d’exploitation Windows utilise pour rechercher une DLL sur le système.

[États du module d’une DLL MFC normale liée de manière dynamique à MFC](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)<br/>
Décrit les États du module d’une DLL MFC normale liée de manière dynamique aux MFC.

[DLL d’extension de MFC](extension-dlls-overview.md)<br/>
Décrit les DLL qui implémentent généralement des classes réutilisables dérivées de classes de bibliothèque MFC existantes.

[Création d’une DLL de ressource uniquement](creating-a-resource-only-dll.md)<br/>
Traite des DLL de ressource uniquement, qui ne contiennent que des ressources, telles que des icônes, des images bitmap, des chaînes et des boîtes de dialogue.

[Ressources localisées dans les applications MFC : DLL satellites](localized-resources-in-mfc-applications-satellite-dlls.md)<br/>
Fournit une prise en charge améliorée pour les DLL satellites, une fonctionnalité qui vous aide à créer des applications localisées pour différentes langues.

[Importation et exportation](importing-and-exporting.md)<br/>
Décrit l'importation de symboles publics dans une application ou l'exportation de fonctions à partir d'une DLL.

[Technologie active et DLL](active-technology-and-dlls.md)<br/>
Autorise l'implémentation des serveurs d'objets dans une DLL.

[Automation dans une DLL](automation-in-a-dll.md)<br/>
Décrit ce que fournit l'option Automation de l'Assistant DLL MFC.

[Conventions d’affectation de noms pour les DLL MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)<br/>
Décrit comment les DLL et les bibliothèques incluses dans les MFC obéissent aux règles d'une convention d'attribution de noms structurée.

[Appel de fonctions DLL à partir d’applications Visual Basic](calling-dll-functions-from-visual-basic-applications.md)<br/>
Explique comment appeler des fonctions DLL à partir d'applications Visual Basic.

## <a name="related-sections"></a>Rubriques connexes

[Utilisation de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)<br/>
Décrit les DLL MFC standard, qui vous permettent d’utiliser la bibliothèque MFC dans le cadre d’une bibliothèque de liens dynamiques Windows.

[Version DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)<br/>
Décrit comment vous pouvez utiliser les bibliothèques de liens dynamiques partagées MFCxx. dll et MFCxxD. dll (où x est le numéro de version MFC) avec les applications MFC et les dll d’extension MFC.
