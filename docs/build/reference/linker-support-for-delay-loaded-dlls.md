---
title: Prise en charge de l'éditeur de liens pour les DLL à chargement différé
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
ms.openlocfilehash: b6e514a6b13aced4fcd765df091810504f948588
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176250"
---
# <a name="linker-support-for-delay-loaded-dlls"></a>Prise en charge de l'éditeur de liens pour les DLL à chargement différé

L’éditeur de liens MSVC prend désormais en charge le chargement différé des DLL. Cela vous évite d’avoir à utiliser les fonctions du Kit de développement logiciel Windows **LoadLibrary** et **GetProcAddress** pour implémenter le chargement différé des DLL.

Avant Visual C++ 6.0, la seule façon de charger une DLL au moment de l’exécution a été à l’aide de **LoadLibrary** et **GetProcAddress**; le système d’exploitation chargerait la DLL lorsque le fichier exécutable ou DLL à l’aide de son chargement.

À compter de Visual C++ 6.0, lors de la liaison implicitement avec une DLL, l’éditeur de liens fournit des options pour différer le chargement de la DLL jusqu'à ce que le programme appelle une fonction dans cette DLL.

Une application peut différer de charger une DLL à l’aide de la [/DELAYLOAD (différer le chargement de l’importation)](delayload-delay-load-import.md) option de l’éditeur de liens avec une fonction d’assistance (implémentation par défaut fournie par Visual C++). La fonction d’assistance charge la DLL au moment de l’exécution en appelant **LoadLibrary** et **GetProcAddress** pour vous.

Vous devez envisager le chargement différé d’une DLL si :

- Votre programme ne peut pas appeler une fonction dans la DLL.

- Une fonction dans la DLL n’est appelée jusqu'à ce que vous en fin de l’exécution de votre programme.

Le chargement différé d’une DLL peut être spécifié pendant la génération d’un. EXE ou. Projet DLL. A. Projet DLL qui diffère le chargement d’une ou plusieurs DLL lui-même n’appelez pas un point d’entrée de chargement différé dans Dllmain.

Les rubriques suivantes décrivent les DLL à chargement différé :

- [Spécification de DLL dont le chargement doit être différé](specifying-dlls-to-delay-load.md)

- [Déchargement explicite d’une DLL à chargement différé](explicitly-unloading-a-delay-loaded-dll.md)

- [Chargement de toutes les importations pour une DLL à chargement différé](loading-all-imports-for-a-delay-loaded-dll.md)

- [Liaison d’importations](binding-imports.md)

- [Gestion et notification des erreurs](error-handling-and-notification.md)

- [Dump des importations à chargement différé](dumping-delay-loaded-imports.md)

- [Contraintes relatives aux DLL à chargement différé](constraints-of-delay-loading-dlls.md)

- [Présentation de la fonction d’assistance](understanding-the-helper-function.md)

- [Développement de votre propre fonction d’assistance](developing-your-own-helper-function.md)

## <a name="see-also"></a>Voir aussi

[DLL dans Visual C++](../dlls-in-visual-cpp.md)<br/>
[Informations de référence sur l’éditeur de liens MSVC](linking.md)
