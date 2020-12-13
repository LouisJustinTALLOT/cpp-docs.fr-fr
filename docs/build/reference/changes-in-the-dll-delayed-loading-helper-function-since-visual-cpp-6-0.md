---
description: En savoir plus sur les modifications apportées à la fonction d’assistance du chargement différé des DLL depuis Visual C++ 6,0
title: Modifications apportées à la fonction d'assistance du chargement différé des DLL depuis Visual C++ 6.0
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
ms.openlocfilehash: 0141467aab0b804cf82d21c15510d8f9941853a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182487"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Modifications apportées à la fonction d'assistance du chargement différé des DLL depuis Visual C++ 6.0

Si vous avez plusieurs versions de Visual C++ sur votre ordinateur ou si vous avez défini votre propre fonction d’assistance, vous risquez d’être affecté par les modifications apportées à la fonction d’assistance de chargement différé de DLL. Par exemple :

- **__delayLoadHelper** est désormais **__delayLoadHelper2**

- **__pfnDliNotifyHook** est désormais **__pfnDliNotifyHook2**

- **__pfnDliFailureHook** est désormais **__pfnDliFailureHook2**

- **__FUnloadDelayLoadedDLL** est désormais **__FUnloadDelayLoadedDLL2**

> [!NOTE]
> Si vous utilisez la fonction d’assistance par défaut, ces modifications ne vous concernent pas. Il n’y a aucune modification concernant l’appel de l’éditeur de liens.

## <a name="multiple-versions-of-visual-c"></a>Plusieurs versions de Visual C++

Si vous avez plusieurs versions de Visual C++ sur votre ordinateur, assurez-vous que l’éditeur de liens correspond à delayimp. lib. En cas d’incompatibilité, vous obtiendrez un rapport d’erreurs de l’éditeur de liens `___delayLoadHelper2@8` ou `___delayLoadHelper@8` comme symbole externe non résolu. Le premier implique un nouvel éditeur de liens avec une ancienne bibliothèque delayimp. lib, et ce dernier implique un ancien éditeur de liens avec un nouveau delayimp. lib.

Si vous obtenez une erreur d’éditeur de liens non résolue, exécutez [DUMPBIN/LINKERMEMBER](linkermember.md): 1 sur delayimp. lib qui devrait contenir la fonction d’assistance pour voir quelle fonction d’assistance est définie à la place. La fonction d’assistance peut également être définie dans un fichier objet ; Exécutez [DUMPBIN/SYMBOLS](symbols.md) et recherchez `delayLoadHelper(2)` .

Si vous savez que vous disposez de l’éditeur de liens Visual C++ 6,0, procédez comme suit :

- Exécutez DUMPBIN sur le fichier. lib ou. obj du programme d’assistance de chargement différé pour déterminer s’il définit **__delayLoadHelper2**. Si ce n’est pas le cas, le lien échoue.

- Définissez **__delayLoadHelper** dans le fichier. lib ou. obj du programme d’assistance de chargement différé.

## <a name="user-defined-helper-function"></a>Fonction d’assistance User-Defined

Si vous avez défini votre propre fonction d’assistance et que vous utilisez la version actuelle de Visual C++, procédez comme suit :

- Renommez la fonction d’assistance en **__delayLoadHelper2**.

- Étant donné que les pointeurs du descripteur de délai (ImgDelayDescr dans delayimp. h) ont été modifiés d’adresses absolues (SAV) vers des adresses relatives (RVA) pour fonctionner comme prévu dans les programmes 32 et 64 bits, vous devez les reconvertir en pointeurs. Une nouvelle fonction a été introduite : PFromRva, qui se trouve dans delayhlp. cpp. Vous pouvez utiliser cette fonction sur chacun des champs du descripteur pour les reconvertir en pointeurs 32 ou 64 bits. La fonction d’assistance de chargement différé par défaut continue d’être un bon modèle à utiliser comme exemple.

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>Charger toutes les importations pour une DLL Delay-Loaded

L’éditeur de liens peut charger toutes les importations à partir d’une DLL que vous avez spécifiée pour un chargement différé. Pour plus d’informations, consultez [chargement de toutes les importations pour une DLL Delay-Loaded](loading-all-imports-for-a-delay-loaded-dll.md) .

## <a name="see-also"></a>Voir aussi

[Fonctionnement de la fonction d’assistance](understanding-the-helper-function.md)
