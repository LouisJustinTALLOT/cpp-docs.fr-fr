---
title: Modifications apportées à la fonction d'assistance du chargement différé des DLL depuis Visual C++ 6.0
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
ms.openlocfilehash: 536729e27c89d068957ea451355957e4a35348ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320608"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Modifications apportées à la fonction d'assistance du chargement différé des DLL depuis Visual C++ 6.0

Si vous avez plusieurs versions de Visual CMD sur votre ordinateur ou si vous avez défini votre propre fonction d’aide, vous pouvez être affecté par les modifications apportées à la fonction d’aide de chargement retardée DLL. Par exemple :

- **__delayLoadHelper** est maintenant **__delayLoadHelper2**

- **__pfnDliNotifyHook** est maintenant **__pfnDliNotifyHook2**

- **__pfnDliFailureHook** est maintenant **__pfnDliFailureHook2**

- **__FUnloadDelayLoadedDLL** est maintenant **__FUnloadDelayLoadedDLL2**

> [!NOTE]
> Si vous utilisez la fonction d’aide par défaut, ces modifications ne vous affecteront pas. Il n’y a aucun changement concernant la façon dont vous invoquez le lien.

## <a name="multiple-versions-of-visual-c"></a>Versions multiples de Visual CM

Si vous avez plusieurs versions de Visual CM SUR votre ordinateur, assurez-vous que le linker correspond à delayimp.lib. S’il y a un décalage, vous obtiendrez `___delayLoadHelper2@8` une `___delayLoadHelper@8` erreur de liaison signalant soit ou comme un symbole externe non résolu. Le premier implique un nouveau lien avec un vieux delayimp.lib, et le second implique un vieux lien avec un nouveau delayimp.lib.

Si vous obtenez une erreur de liaison non résolue, exécutez [dumpbin /linkermember](linkermember.md):1 sur le delayimp.lib que vous vous attendez à contenir la fonction d’aide pour voir quelle fonction d’aide est définie à la place. La fonction d’aide peut également être définie dans un fichier d’objets; exécuter [dumpbin / symboles](symbols.md) et chercher `delayLoadHelper(2)`.

Si vous savez que vous avez le lien visuel C 6.0, alors:

- Exécuter dumpbin sur le fichier .lib ou .obj de charge de retard pour déterminer s’il définit **__delayLoadHelper2**. Si ce n’est pas le cas, le lien échouera.

- Définir **__delayLoadHelper** dans le fichier .lib ou .obj de l’aide de charge de retard.

## <a name="user-defined-helper-function"></a>Fonction d’aide définie par l’utilisateur

Si vous définissez votre propre fonction d’aide et utilisez la version actuelle de Visual CMD, faites ce qui suit :

- Renommer la fonction d’aide pour **__delayLoadHelper2**.

- Depuis les pointeurs dans le descripteur de retard (ImgDelayDescr dans delayimp.h) ont été changés d’adresses absolues (VAs) à des adresses relatives (RVAs) pour travailler comme prévu dans les deux programmes 32 et 64 bits, vous devez convertir ces retour à des pointeurs. Une nouvelle fonction a été introduite: PFromRva, trouvé dans delayhlp.cpp. Vous pouvez utiliser cette fonction sur chacun des champs du descripteur pour les convertir en pointeurs 32 ou 64 bits. La fonction d’aide à la charge de retard par défaut continue d’être un bon modèle à utiliser à titre d’exemple.

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>Chargez toutes les importations pour un DLL chargé de retard

Le lien peut charger toutes les importations à partir d’un DLL que vous avez spécifié pour être chargé de retard. Voir [Chargement de toutes les importations pour un DLL chargé de retard](loading-all-imports-for-a-delay-loaded-dll.md) pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Présentation de la fonction d’assistance](understanding-the-helper-function.md)
