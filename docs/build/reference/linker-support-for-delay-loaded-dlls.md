---
description: 'En savoir plus sur : prise en charge de l’éditeur de liens pour les dll Delay-Loaded'
title: Prise en charge de l'éditeur de liens pour les DLL à chargement différé
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
ms.openlocfilehash: 6bf4527d14c7313874f162f0597114132b1a81cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190963"
---
# <a name="linker-support-for-delay-loaded-dlls"></a>Prise en charge de l'éditeur de liens pour les DLL à chargement différé

L’éditeur de liens MSVC prend désormais en charge le chargement différé des dll. Cela vous évite d’avoir à utiliser les fonctions SDK Windows **LoadLibrary** et **GetProcAddress** pour implémenter le chargement différé des dll.

Avant le Visual C++ 6,0, le seul moyen de charger une DLL au moment de l’exécution était d’utiliser **LoadLibrary** et **GetProcAddress**. le système d’exploitation chargera la DLL lors du chargement de l’exécutable ou de la DLL qui l’utilise.

À partir de Visual C++ 6,0, lorsque vous établissez une liaison implicite avec une DLL, l’éditeur de liens fournit des options pour différer le chargement de la DLL jusqu’à ce que le programme appelle une fonction dans cette DLL.

Une application peut retarder le chargement d’une DLL à l’aide de l’option de l’éditeur de liens [/delayload (différer le chargement de l’importation)](delayload-delay-load-import.md) avec une fonction d’assistance (implémentation par défaut fournie par Visual C++). La fonction d’assistance chargera la DLL au moment de l’exécution en appelant **LoadLibrary** et **GetProcAddress** pour vous.

Vous devez envisager de retarder le chargement d’une DLL dans les cas suivants :

- Votre programme ne peut pas appeler une fonction dans la DLL.

- Une fonction dans la DLL ne peut pas être appelée jusqu’à la fin de l’exécution de votre programme.

Le chargement différé d’une DLL peut être spécifié pendant la génération d’un. EXE ou. Projet DLL. Un. Un projet DLL qui retarde le chargement d’une ou plusieurs dll ne doit pas lui-même appeler un point d’entrée à chargement différé dans DllMain.

Les rubriques suivantes décrivent le chargement différé des dll :

- [Spécification des dll pour différer le chargement](specifying-dlls-to-delay-load.md)

- [Déchargement explicite d’une DLL Delay-Loaded](explicitly-unloading-a-delay-loaded-dll.md)

- [Chargement de toutes les importations pour une DLL Delay-Loaded](loading-all-imports-for-a-delay-loaded-dll.md)

- [Liaison d’importations](binding-imports.md)

- [Gestion et notification des erreurs](error-handling-and-notification.md)

- [Vidage des importations Delay-Loaded](dumping-delay-loaded-imports.md)

- [Contraintes de chargement différé des dll](constraints-of-delay-loading-dlls.md)

- [Fonctionnement de la fonction d’assistance](understanding-the-helper-function.md)

- [Développement de votre propre fonction d’assistance](developing-your-own-helper-function.md)

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](../dlls-in-visual-cpp.md)<br/>
[Informations de référence sur l’éditeur de liens MSVC](linking.md)
