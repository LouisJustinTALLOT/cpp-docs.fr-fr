---
description: 'En savoir plus sur : présentation de la fonction d’assistance'
title: Présentation de la fonction d'assistance
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
ms.openlocfilehash: d47e392d78d6cf872af28b992885c57d34bddf0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247096"
---
# <a name="understanding-the-helper-function"></a>Présentation de la fonction d'assistance

La fonction d’assistance pour le chargement différé pris en charge par l’éditeur de liens est ce qui charge réellement la DLL au moment de l’exécution. Vous pouvez modifier la fonction d’assistance pour personnaliser son comportement en écrivant votre propre fonction et en la liant à votre programme au lieu d’utiliser la fonction d’assistance fournie dans delayimp. lib. Une fonction d’assistance dessert toutes les dll à chargement différé.

Vous pouvez fournir votre propre version de la fonction d’assistance Si vous souhaitez effectuer un traitement spécifique en fonction des noms de la DLL ou des importations.

La fonction d’assistance effectue les actions suivantes :

- Vérifie le descripteur stocké dans la bibliothèque pour voir s’il a déjà été chargé

- Appelle **LoadLibrary** pour tenter de charger la dll

- Appelle **GetProcAddress** pour tenter d’obtenir l’adresse de la procédure

- Retourne au thunk de chargement différé d’importation pour appeler le point d’entrée chargé maintenant

La fonction d’assistance peut rappeler un hook de notification dans votre programme après chacune des actions suivantes :

- Lors du démarrage de la fonction d’assistance

- Juste avant l’appel de **LoadLibrary** dans la fonction d’assistance

- Juste avant l’appel de **GetProcAddress** dans la fonction d’assistance

- En cas d’échec de l’appel à **LoadLibrary** dans la fonction d’assistance

- En cas d’échec de l’appel à **GetProcAddress** dans la fonction d’assistance

- Après le traitement de la fonction d’assistance

Chacun de ces points de raccordement peut retourner une valeur qui modifie le traitement normal de la routine d’assistance d’une manière ou d’une autres, à l’exception du retour au thunk de chargement d’importation différée.

Le code d’assistance par défaut se trouve dans delayhlp. cpp et delayimp. h (dans vc\include) et est compilé dans delayimp. lib (dans vc\lib). Vous devrez inclure cette bibliothèque dans vos compilations, sauf si vous écrivez votre propre fonction d’assistance.

Les rubriques suivantes décrivent la fonction d’assistance :

- [Modifications apportées à la fonction d’assistance de chargement différé des DLL depuis Visual C++ 6,0](changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)

- [Conventions d’appel, paramètres et type de retour](calling-conventions-parameters-and-return-type.md)

- [Définitions de structure et de constante](structure-and-constant-definitions.md)

- [Calcul des valeurs nécessaires](calculating-necessary-values.md)

- [Déchargement d’une DLL Delay-Loaded](explicitly-unloading-a-delay-loaded-dll.md)

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les dll Delay-Loaded](linker-support-for-delay-loaded-dlls.md)
