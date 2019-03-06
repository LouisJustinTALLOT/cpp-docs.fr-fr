---
title: Prise en charge de l'éditeur de liens pour les DLL à chargement différé
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
ms.openlocfilehash: 3fddc749c1e03b0f21c74f922943713d52339679
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421153"
---
# <a name="linker-support-for-delay-loaded-dlls"></a>Prise en charge de l'éditeur de liens pour les DLL à chargement différé

L’éditeur de liens Visual C++ prend désormais en charge le chargement différé des DLL. Cela vous évite d’avoir à utiliser les fonctions du Kit de développement logiciel Windows **LoadLibrary** et **GetProcAddress** pour implémenter le chargement différé des DLL.

Avant Visual C++ 6.0, la seule façon de charger une DLL au moment de l’exécution a été à l’aide de **LoadLibrary** et **GetProcAddress**; le système d’exploitation chargerait la DLL lorsque le fichier exécutable ou DLL à l’aide de son chargement.

À compter de Visual C++ 6.0, lors de la liaison implicitement avec une DLL, l’éditeur de liens fournit des options pour différer le chargement de la DLL jusqu'à ce que le programme appelle une fonction dans cette DLL.

Une application peut différer de charger une DLL à l’aide de la [/DELAYLOAD (différer le chargement de l’importation)](../../build/reference/delayload-delay-load-import.md) option de l’éditeur de liens avec une fonction d’assistance (implémentation par défaut fournie par Visual C++). La fonction d’assistance charge la DLL au moment de l’exécution en appelant **LoadLibrary** et **GetProcAddress** pour vous.

Vous devez envisager le chargement différé d’une DLL si :

- Votre programme ne peut pas appeler une fonction dans la DLL.

- Une fonction dans la DLL n’est appelée jusqu'à ce que vous en fin de l’exécution de votre programme.

Le chargement différé d’une DLL peut être spécifié pendant la génération d’un. EXE ou. Projet DLL. A. Projet DLL qui diffère le chargement d’une ou plusieurs DLL lui-même n’appelez pas un point d’entrée de chargement différé dans Dllmain.

Les rubriques suivantes décrivent les DLL à chargement différé :

- [Spécification de DLL dont le chargement doit être différé](../../build/reference/specifying-dlls-to-delay-load.md)

- [Déchargement explicite d’une DLL à chargement différé](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)

- [Chargement de toutes les importations pour une DLL à chargement différé](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)

- [Liaison d’importations](../../build/reference/binding-imports.md)

- [Gestion et notification des erreurs](../../build/reference/error-handling-and-notification.md)

- [Dump des importations à chargement différé](../../build/reference/dumping-delay-loaded-imports.md)

- [Contraintes relatives aux DLL à chargement différé](../../build/reference/constraints-of-delay-loading-dlls.md)

- [Présentation de la fonction d’assistance](understanding-the-helper-function.md)

- [Développement de votre propre fonction d’assistance](../../build/reference/developing-your-own-helper-function.md)

## <a name="see-also"></a>Voir aussi

[DLL dans Visual C++](../../build/dlls-in-visual-cpp.md)<br/>
[Liaison](../../build/reference/linking.md)
