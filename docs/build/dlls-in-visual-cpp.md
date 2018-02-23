---
title: DLL en Visual C++ | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 14f8a0914b1bb7f2d3a16681a3a66091eda71d73
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2018
---
# <a name="dlls-in-visual-c"></a>DLL en Visual C++  
  
Dans Windows, une bibliothèque de liens dynamiques (DLL) est un type de fichier exécutable qui agit comme une bibliothèque partagée de fonctions et de ressources. La liaison dynamique est une fonctionnalité du système d’exploitation qui permet à un fichier exécutable appeler des fonctions ou utiliser des ressources stockées dans un fichier distinct. Ces fonctions et ressources peuvent être compilées et déployées séparément des exécutables qui les utilisent. Une DLL n’est pas un exécutable autonome ; Il s’exécute dans le contexte d’une application qui l’appelle. Le système d’exploitation peut charger la DLL dans l’espace mémoire d’une application lors du chargement de l’application (*liaison implicite*), ou à la demande lors de l’exécution (*liaison explicite*). Les DLL facilitent également le partage des fonctions et des ressources entre les fichiers exécutables. Plusieurs applications peuvent accéder simultanément au contenu d'une copie de la DLL en mémoire.  
  
## <a name="differences-between-dynamic-linking-and-static-linking"></a>Différences entre la liaison dynamique et la liaison statique  
  
Liaison statique copie tout le code de l’objet dans une bibliothèque statique dans les fichiers exécutables qui l’utilisent lorsqu’elles sont générées. La liaison dynamique inclut uniquement les informations requises par Windows en cours d’exécution pour localiser et charger la DLL qui contient un élément de données ou une fonction. Lorsque vous créez une DLL, vous créez également une bibliothèque d’importation qui contient ces informations. Lorsque vous générez un fichier exécutable qui appelle la DLL, l’éditeur de liens utilise les symboles exportés dans la bibliothèque d’importation pour stocker ces informations pour le chargeur Windows. Lorsque le chargeur charge une DLL, la DLL est mappée dans l’espace de mémoire de votre application. Le cas échéant, un spécial de fonction dans la DLL, `DllMain`, est appelée pour effectuer toute initialisation requise par la DLL.  
  
<a name="differences-between-applications-and-dlls"></a>  
  
## <a name="differences-between-applications-and-dlls"></a>Différences entre les applications et les DLL  
  
Bien que les DLL et les applications sont les deux modules exécutables, elles diffèrent de plusieurs façons. À l’utilisateur final, la différence la plus évidente est que les DLL ne sont pas des applications qui peuvent être exécutées directement. À partir du point de vue système, il existe deux différences fondamentales entre les applications et les DLL :  
  
-   Une application peut avoir plusieurs instances d’exécution dans le système simultanément, tandis qu’une DLL peut avoir qu’une seule instance.  
  
-   Une application peut être chargée en tant que processus possédant des éléments tels que la pile, les threads de l’exécution, la mémoire globale, des descripteurs de fichiers et une file d’attente, mais une DLL ne peut pas.  
  
<a name="advantages-of-using-dlls"></a>  
  
## <a name="advantages-of-using-dlls"></a>Avantages de l’utilisation des DLL  
  
Au lieu de la liaison statique au code et de ressources à la liaison dynamique offre plusieurs avantages. Quand vous utilisez des DLL, vous pouvez économiser de l'espace mémoire et réduire l'échange. Quand plusieurs applications peuvent utiliser une même copie d'une DLL, vous pouvez économiser de l'espace disque et de la bande passante. Vous pouvez déployer et mettre à jour les DLL séparément, ce qui vous permet de fournir un support après-vente et des mises à jour logicielles sans avoir à regénérer et à fournir tout votre code. Les DLL constituent un moyen pratique de fournir des ressources spécifiques aux paramètres régionaux, qui peuvent prendre en charge les programmes multilingues, et elles facilitent la création de versions internationales de vos applications. Liaison explicite peut permettre à votre application détecter et charger des DLL lors de l’exécution, telles que les extensions qui offrent de nouvelles fonctionnalités.  
  
La liaison dynamique offre les avantages suivants :  
  
-   La liaison dynamique économise de la mémoire et réduit l’échange. De nombreux processus peuvent utiliser une DLL simultanément, partager une seule copie des parties en lecture seule d’une DLL en mémoire. En revanche, chaque application générée à l’aide d’une bibliothèque liée statiquement possède une copie complète du code de bibliothèque Windows doit charger en mémoire.  
  
-   Liaison dynamique permet d’économiser la bande passante et l’espace disque. De nombreuses applications peuvent partager une seule copie de la DLL sur le disque. En revanche, chaque application générée à l’aide d’une bibliothèque de liens statiques a le code de bibliothèque lié à son image exécutable, qui utilise plus d’espace disque et prend plus de bande passante à transférer.  
  
-   Correctifs de maintenance, sécurité et mises à niveau peuvent être plus faciles. Lorsque vos applications utilisent les fonctions communes dans une DLL, puis tant que les arguments de fonction et les valeurs de retour ne changent pas, vous pouvez implémenter des correctifs de bogues et déployer des mises à jour à la DLL. Lors de la DLL sont mis à jour, les applications qui les utilisent n’avez pas besoin d’être recompilées ni lié à nouveau, et ils recourent à la nouvelle DLL dès qu’il est déployé. En revanche, vous effectuez dans le code objet lié statiquement des correctifs vous amener à rétablir les liens et redéployer toutes les applications qui l’utilise.  
  
-   Vous pouvez utiliser la DLL pour fournir un support après-vente. Par exemple, un pilote d’affichage DLL sont modifiables pour prendre en charge d’un affichage qui n’était pas disponible lorsque l’application a été expédiée. Vous pouvez utiliser la liaison explicite pour charger des extensions d’application en tant que DLL et ajouter de nouvelles fonctionnalités à votre application sans la reconstruction ou la redéployer.  
  
-   La liaison dynamique facilite la prise en charge des applications écrites dans différents langages de programmation. Programmes écrits dans différents langages de programmation peuvent appeler la même fonction DLL tant que les programmes suivent la convention d’appel de la fonction. Les programmes et la fonction DLL doivent être compatibles de plusieurs manières : l’ordre dans lequel la fonction attend que ses arguments à être placé sur la pile, si la fonction ou l’application est responsable du nettoyage de la pile et si tous les arguments sont passés dans les registres.  
  
-   La liaison dynamique fournit un mécanisme pour étendre des classes de la bibliothèque MFC. Vous pouvez dériver des classes à partir de classes MFC existantes et les placer dans une DLL d’extension MFC pour une utilisation par les applications MFC.  
  
-   La liaison dynamique facilite la création de versions internationales de votre application. En plaçant des ressources spécifiques aux paramètres régionaux dans une DLL, il est beaucoup plus facile de créer des versions internationales d’une application. Au lieu de livraison de nombreuses versions localisées de votre application, vous pouvez placer les chaînes et les images pour chaque langue dans une DLL de ressources distinct, et ensuite votre application peut charger les ressources appropriées pour ces paramètres régionaux lors de l’exécution.   
  
 Un inconvénient potentiel pour l’utilisation des DLL est que l’application n’est pas autonome ; il dépend de l’existence d’un module DLL distinct que vous devez déployer ou vérifiez vous-même en tant que partie de votre installation.  
  
  
## <a name="more-information-on-how-to-create-and-use-dlls"></a>Plus d’informations sur la façon de créer et utiliser des DLL  
  
Les rubriques suivantes fournissent des informations détaillées sur la programmation des DLL dans Visual C++.  
  
 [Procédure pas à pas : création et utilisation d’une bibliothèque de liens dynamiques (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)  
 Montre comment créer et utiliser une DLL à l'aide de Visual Studio.  
  
 [Genres de DLL](../build/kinds-of-dlls.md)  
 Fournit des informations sur les différentes sortes de DLL qui peuvent être générées.  
  
 [Forum aux Questions de DLL](../build/dll-frequently-asked-questions.md)  
 Fournit des réponses à des questions fréquentes concernant les DLL.  
  
 [Lier un exécutable à une DLL](../build/linking-an-executable-to-a-dll.md)  
 Décrit la liaison explicite et implicite à une DLL.  
  
 [Initialiser une DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
 Présente le code d’initialisation de DLL qui doit s’exécuter lorsque le chargement de la DLL.  
  
 [DLL et comportement de la bibliothèque runtime Visual C++](../build/run-time-library-behavior.md)  
 Décrit comment la bibliothèque Runtime exécute la séquence de démarrage de la DLL.  
  
 [LoadLibrary et AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
 Explique comment utiliser **LoadLibrary** et `AfxLoadLibrary` pour une liaison explicite à une DLL lors de l’exécution.  
  
 [GetProcAddress](../build/getprocaddress.md)  
 Explique comment utiliser **GetProcAddress** pour obtenir l’adresse d’une fonction exportée dans la DLL.  
  
 [FreeLibrary et AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
 Explique comment utiliser **FreeLibrary** et `AfxFreeLibrary` lorsque le module DLL n’est plus nécessaire.  
  
 [Chemin de recherche utilisé par Windows pour localiser une DLL](../build/search-path-used-by-windows-to-locate-a-dll.md)  
 Décrit le chemin d’accès que le système d’exploitation Windows utilise pour rechercher une DLL sur le système.  
  
 [États du module d’une DLL MFC normale liée de manière dynamique à MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
 Décrit les États du module d’une expression régulière que MFC DLL liée dynamiquement à MFC.  
  
 [DLL d’extension de MFC](../build/extension-dlls-overview.md)  
 Décrit les DLL qui implémentent généralement des classes réutilisables dérivées de classes de bibliothèque MFC existantes.  
  
 [Création d’une DLL de ressource uniquement](../build/creating-a-resource-only-dll.md)  
 Traite des DLL de ressource uniquement, qui ne contiennent que des ressources, telles que des icônes, des images bitmap, des chaînes et des boîtes de dialogue.  
  
 [Ressources localisées dans les applications MFC : DLL satellites](../build/localized-resources-in-mfc-applications-satellite-dlls.md)  
 Fournit une prise en charge améliorée pour les DLL satellites, une fonctionnalité qui vous aide à créer des applications localisées pour différentes langues.  
  
 [Importation et exportation](../build/importing-and-exporting.md)  
 Décrit l'importation de symboles publics dans une application ou l'exportation de fonctions à partir d'une DLL.  
  
 [Technologie active et DLL](../build/active-technology-and-dlls.md)  
 Autorise l'implémentation des serveurs d'objets dans une DLL.  
  
 [Automation dans une DLL](../build/automation-in-a-dll.md)  
 Décrit ce que fournit l'option Automation de l'Assistant DLL MFC.  
  
 [Conventions d’affectation de noms pour les DLL MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)  
 Décrit comment les DLL et les bibliothèques incluses dans les MFC obéissent aux règles d'une convention d'attribution de noms structurée.  
  
 [Appel de fonctions DLL à partir d’Applications Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md)  
 Explique comment appeler des fonctions DLL à partir d'applications Visual Basic.  
  
## <a name="related-sections"></a>Rubriques connexes  
  
 [Utilisation de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
 Décrit les DLL MFC standard, qui vous permettent d’utiliser la bibliothèque MFC dans le cadre d’une bibliothèque de liens dynamiques Windows.  
  
 [Version DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)  
 Décrit comment vous pouvez utiliser le partagées MFCxx.dll et MFCxxD.dll (où x est le numéro de version MFC) des bibliothèques de liens dynamiques avec les applications MFC et les DLL d’extension MFC.  
