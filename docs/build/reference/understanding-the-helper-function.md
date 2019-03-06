---
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
ms.openlocfilehash: 955ae0ed8feac22da19eb13218e2332849477e29
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421379"
---
# <a name="understanding-the-helper-function"></a>Présentation de la fonction d'assistance

La fonction d’assistance pour la prise en charge de l’éditeur de liens le chargement différé est ce qui charge réellement la DLL en cours d’exécution. Vous pouvez modifier la fonction d’assistance pour personnaliser son comportement en écrivant votre propre fonction et en le liant à votre programme au lieu d’utiliser la fonction d’assistance fournie dans Delayimp.lib. Une fonction d’assistance sert toutes les DLL à chargement différé.

Vous pouvez fournir votre propre version de la fonction d’assistance si vous souhaitez effectuer un traitement particulier selon les noms des DLL ou des importations.

La fonction d’assistance effectue les actions suivantes :

- Vérification du handle stocké à la bibliothèque pour voir s’il a déjà été chargé.

- Appels **LoadLibrary** pour tenter de chargement de la DLL

- Appels **GetProcAddress** pour tenter d’obtenir l’adresse de la procédure

- Conversion de code pour appeler le point d’entrée chargé de charge retourne à l’importation de délai

La fonction d’assistance peut rappeler un raccordement de notification dans votre programme lorsque chacune des actions suivantes :

- Au démarrage de la fonction d’assistance

- Juste avant **LoadLibrary** est appelée dans la fonction d’assistance

- Juste avant **GetProcAddress** est appelée dans la fonction d’assistance

- Si l’appel à **LoadLibrary** dans la fonction d’assistance a échoué

- Si l’appel à **GetProcAddress** dans la fonction d’assistance a échoué

- Après l’application d’assistance s’effectue fonction traitement

Chacun de ces points de raccordement peut retourner une valeur qui modifie le traitement normal de la routine d’assistance de quelque façon, sauf le retour au thunk de chargement différé.

Le code d’assistance par défaut peut être trouvé dans Delayhlp.cpp et Delayimp.h (dans vc\include) et est compilé dans Delayimp.lib (dans vc\lib). Vous devez inclure cette bibliothèque dans vos compilations, sauf si vous écrivez votre propre fonction d’assistance.

Les rubriques suivantes décrivent la fonction d’assistance :

- [Modifications apportées à la fonction d’assistance du chargement différé des DLL depuis Visual C++ 6.0](../../build/reference/changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)

- [Conventions d’appel, paramètres et type de retour](../../build/reference/calling-conventions-parameters-and-return-type.md)

- [Définitions des structures et constantes](../../build/reference/structure-and-constant-definitions.md)

- [Calcul des valeurs nécessaires](../../build/reference/calculating-necessary-values.md)

- [Déchargement d’une DLL à chargement différé](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les DLL à chargement différé](../../build/reference/linker-support-for-delay-loaded-dlls.md)
