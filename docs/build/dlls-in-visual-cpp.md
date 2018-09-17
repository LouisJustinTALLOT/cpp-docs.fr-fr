---
title: DLL dans Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28be2caa3477eabc8b717b387c99d65585a9ef19
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718053"
---
# <a name="dlls-in-visual-c"></a>DLL en Visual C++

Dans Windows, une bibliothèque de liens dynamiques (DLL) est un type de fichier exécutable qui agit comme une bibliothèque partagée de fonctions et de ressources. La liaison dynamique est une fonctionnalité du système d’exploitation qui permet à un fichier exécutable appeler des fonctions ou utiliser des ressources stockées dans un fichier distinct. Ces fonctions et ressources peuvent être compilées et déployées séparément des exécutables qui les utilisent. Une DLL n’est pas un exécutable autonome ; Il s’exécute dans le contexte d’une application qui l’appelle. Le système d’exploitation peut charger la DLL dans l’espace de mémoire d’une application lors du chargement de l’application (*liaison implicite*), ou à la demande lors de l’exécution (*liaison explicite*). Les DLL facilitent également le partage des fonctions et des ressources entre les fichiers exécutables. Plusieurs applications peuvent accéder simultanément au contenu d'une copie de la DLL en mémoire.

## <a name="differences-between-dynamic-linking-and-static-linking"></a>Différences entre la liaison dynamique et la liaison statique

Liaison statique copie tout le code de l’objet dans une bibliothèque statique dans les fichiers exécutables qui l’utilisent lorsqu’elles sont générées. Liaison dynamique inclut uniquement les informations requises par Windows en cours d’exécution pour localiser et charger la DLL qui contient un élément de données ou la fonction. Lorsque vous créez une DLL, vous créez également une bibliothèque d’importation qui contient ces informations. Lorsque vous générez un fichier exécutable qui appelle la DLL, l’éditeur de liens utilise les symboles exportés dans la bibliothèque d’importation pour stocker ces informations pour le chargeur de Windows. Lorsque le chargeur charge une DLL, la DLL est mappée dans l’espace de mémoire de votre application. Le cas échéant, un spécial de fonction dans la DLL, `DllMain`, est appelée pour effectuer toute initialisation requise par la DLL.

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>Différences entre les applications et les DLL

Bien que les DLL et les applications sont les deux modules exécutables, elles diffèrent de plusieurs façons. À l’utilisateur final, la différence la plus évidente est que les DLL ne sont pas des applications qui peuvent être exécutées directement. À partir du point de vue système, il existe deux différences fondamentales entre les applications et les DLL :

- Une application peut avoir plusieurs instances d’exécution dans le système simultanément, tandis qu’une DLL peut avoir qu’une seule instance.

- Une application peut être chargée en tant que processus qui peuvent posséder des choses comme une pile, les threads de l’exécution, de mémoire globale, de descripteurs de fichiers et d’une file d’attente, mais une DLL ne peut pas.

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Avantages de l’utilisation de DLL

Liaison dynamique au lieu de la liaison statique au code et de ressources offre plusieurs avantages. Quand vous utilisez des DLL, vous pouvez économiser de l'espace mémoire et réduire l'échange. Quand plusieurs applications peuvent utiliser une même copie d'une DLL, vous pouvez économiser de l'espace disque et de la bande passante. Vous pouvez déployer et mettre à jour les DLL séparément, ce qui vous permet de fournir un support après-vente et des mises à jour logicielles sans avoir à regénérer et à fournir tout votre code. Les DLL constituent un moyen pratique de fournir des ressources spécifiques aux paramètres régionaux, qui peuvent prendre en charge les programmes multilingues, et elles facilitent la création de versions internationales de vos applications. Liaison explicite peut permettre à votre application détecter et charger des DLL lors de l’exécution, telles que les extensions qui offrent de nouvelles fonctionnalités.

La liaison dynamique offre les avantages suivants :

- Liaison dynamique économise de la mémoire et réduit l’échange. De nombreux processus peuvent utiliser une DLL simultanément, partager une seule copie des parties d’une DLL en mémoire en lecture seule. En revanche, chaque application est générée à l’aide d’une bibliothèque liée statiquement possède une copie complète du code de bibliothèque qui Windows doit charger en mémoire.

- Liaison dynamique permet d’économiser la bande passante et l’espace disque. De nombreuses applications peuvent partager une seule copie de la DLL sur le disque. En revanche, chaque application générée à l’aide d’une bibliothèque de liens statiques a le code de bibliothèque lié à son image exécutable, qui utilise davantage d’espace disque et prend plus de bande passante à transférer.

- Maintenance, les correctifs de sécurité et mises à niveau peuvent être plus faciles. Lorsque vos applications utilisent des fonctions communes dans une DLL, puis tant que les arguments de fonction et les valeurs de retour ne changent pas, vous pouvez implémenter des correctifs de bogues et déployer des mises à jour à la DLL. Lors de la DLL sont mis à jour, les applications qui les utilisent n’avez pas besoin d’être recompilées ni lié à nouveau, et ils recourent à la nouvelle DLL dès qu’elle est déployée. En revanche, vous apportez dans le code de l’objet lié statiquement des correctifs vous obligent à relier et redéployer toutes les applications qui l’utilise.

- Vous pouvez utiliser la DLL pour prendre en charge après-vente. Par exemple, un pilote d’affichage DLL peut être modifié pour prendre en charge un affichage qui n’était pas disponible lorsque l’application a été livrée. Vous pouvez utiliser la liaison explicite pour charger des extensions d’application en tant que DLL et ajouter de nouvelles fonctionnalités à votre application sans reconstruction ou de la redéployer.

- Liaison dynamique rend plus facile prendre en charge les applications écrites dans différents langages de programmation. Les programmes écrits dans différents langages de programmation peuvent appeler la même fonction DLL tant que les programmes suivent la convention d’appel de la fonction. Les programmes et la fonction DLL doivent être compatibles de plusieurs manières : l’ordre dans lequel la fonction attend que ses arguments de la pile, si la fonction ou l’application est chargée du nettoyage de la pile et si tous les arguments sont passés dans les registres.

- Liaison dynamique fournit un mécanisme permettant d’étendre les classes de la bibliothèque MFC. Vous pouvez dériver des classes à partir de classes MFC existantes et les placer dans une DLL d’extension MFC pour une utilisation par les applications MFC.

- Liaison dynamique facilite la création de versions internationales de votre application. En plaçant les ressources locales dans une DLL, il est beaucoup plus facile de créer des versions internationales d’une application. Au lieu d’expédition de nombreuses versions localisées de votre application, vous pouvez placer les chaînes et des images pour chaque langue dans une DLL de ressource distinct, et ensuite votre application peut charger les ressources appropriées pour ces paramètres régionaux lors de l’exécution.

Un inconvénient potentiel à l’utilisation des DLL est que l’application n’est pas autonome ; Cela dépend de l’existence d’un module DLL distinct que vous devez déployer ou vérifier vous-même dans le cadre de votre installation.

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Plus d’informations sur la façon de créer et utiliser des DLL

Les rubriques suivantes fournissent des informations détaillées sur la programmation des DLL dans Visual C++.

[Procédure pas à pas : Création et utilisation d’une bibliothèque de liens dynamiques (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md) décrit comment créer et utiliser une DLL à l’aide de Visual Studio.

[Types de DLL](../build/kinds-of-dlls.md) fournit des informations sur les différents types de DLL qui peuvent être générées.

[Forum aux Questions DLL](../build/dll-frequently-asked-questions.md) fournit des réponses aux questions fréquemment posées sur les DLL.

[Lier un exécutable à une DLL](../build/linking-an-executable-to-a-dll.md) décrit la liaison explicite et implicite à une DLL.

[Initialiser une DLL](../build/run-time-library-behavior.md#initializing-a-dll) traite l’initialisation code de la DLL qui doit s’exécuter lorsque le chargement de la DLL.

[DLL et comportement de la bibliothèque d’exécution Visual C++](../build/run-time-library-behavior.md) décrit comment la bibliothèque Runtime exécute la séquence de démarrage DLL.

[LoadLibrary et AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md) explique l’utilisation de **LoadLibrary** et `AfxLoadLibrary` pour une liaison explicite à une DLL lors de l’exécution.

[GetProcAddress](../build/getprocaddress.md) explique l’utilisation de **GetProcAddress** pour obtenir l’adresse d’une fonction exportée dans la DLL.

[FreeLibrary et AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md) explique l’utilisation de **FreeLibrary** et `AfxFreeLibrary` lorsque le module DLL n’est plus nécessaire.

[Dynamic-Link Library Search Order](/windows/desktop/Dlls/dynamic-link-library-search-order) décrit le chemin de recherche, le système d’exploitation Windows utilise pour rechercher une DLL sur le système.

[États du module d’un régulière MFC DLL liés de manière dynamique aux MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md) décrit les États du module d’une expression régulière MFC DLL liée de manière dynamique aux MFC.

[DLL d’extension MFC](../build/extension-dlls-overview.md) explique les DLL qui implémente généralement des classes réutilisables dérivées de classes Microsoft Foundation Class Library existantes.

[Création d’une DLL Resource-Only](../build/creating-a-resource-only-dll.md) traite une DLL de ressource uniquement, qui ne contient que des ressources, telles que des icônes, des bitmaps, des chaînes et des boîtes de dialogue.

[Ressources localisées dans des Applications MFC : DLL satellites](../build/localized-resources-in-mfc-applications-satellite-dlls.md) fournit meilleure prise en charge pour les DLL satellites, une fonctionnalité qui vous aide à créer des applications localisées pour différentes langues.

[Importation et exportation](../build/importing-and-exporting.md) décrit l’importation de symboles publics dans une application ou d’exportation de fonctions à partir d’une DLL

[Technologie active et les DLL](../build/active-technology-and-dlls.md) permet aux serveurs d’objet à mettre en œuvre à l’intérieur d’une DLL.

[Automation dans une DLL](../build/automation-in-a-dll.md) décrit ce que fournit l’option Automation de l’Assistant DLL MFC.

[Conventions de nommage pour les DLL MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions) explique comment les DLL et les bibliothèques incluses dans les MFC suivent une convention d’affectation de noms structurée.

[Appel des fonctions DLL à partir d’Applications Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md) décrit comment appeler des fonctions DLL à partir d’applications Visual Basic.

## <a name="related-sections"></a>Rubriques connexes

[À l’aide de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md) décrit des DLL MFC normales, ce qui vous permettent d’utiliser la bibliothèque MFC dans le cadre d’une bibliothèque de liens dynamiques Windows.

[Version DLL de MFC](../mfc/tn033-dll-version-of-mfc.md) décrit comment vous pouvez utiliser la MFCxx.dll et MFCxxD.dll (où x est le numéro de version MFC) partagé des bibliothèques de liens dynamiques avec les applications MFC et les DLL d’extension MFC.
