---
description: 'En savoir plus sur : liaison au CRT dans votre projet ATL'
title: Liaison vers le CRT dans votre projet ATL
ms.date: 11/04/2016
helpviewer_keywords:
- CRT, linking with ATL
- WinMainCRTStartup method
- DllMainCRTStartup method
- wWinMainCRTStartup method
- ATL, C Run-Time library (CRT)
ms.assetid: 650957ae-362c-4ecf-8b03-5d49138e8b5b
ms.openlocfilehash: e54301332d9a83546e41ab42169f06d305bbc6a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147626"
---
# <a name="linking-to-the-crt-in-your-atl-project"></a>Liaison vers le CRT dans votre projet ATL

Les [bibliothèques de Run-Time C](../c-runtime-library/crt-library-features.md) (CRT) fournissent de nombreuses fonctions utiles qui facilitent grandement la programmation pendant le développement ATL. Tous les projets ATL sont liés à la bibliothèque CRT. Vous pouvez voir les avantages et les inconvénients de la méthode de liaison dans [les avantages et les compromis de la méthode utilisée pour établir un lien vers la bibliothèque CRT](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md).

## <a name="effects-of-linking-to-the-crt-on-your-program-image"></a>Effets de la liaison à la bibliothèque CRT sur votre image de programme

Si vous effectuez un lien statique vers la bibliothèque CRT, le code du CRT est placé dans votre image exécutable et il n’est pas nécessaire que la DLL CRT soit présente sur un système pour exécuter votre image. Si vous effectuez un lien dynamique vers le CRT, les références au code dans la DLL CRT sont placées dans votre image, mais pas dans le code lui-même. Pour que votre image s’exécute sur un système donné, la DLL CRT doit être présente sur ce système. Même lorsque vous liez dynamiquement à la bibliothèque CRT, vous constaterez peut-être que du code peut être lié de manière statique (par exemple, `DllMainCRTStartup` ).

Quand vous liez votre image, vous spécifiez explicitement ou implicitement un point d’entrée que le système d’exploitation appellera après le chargement de l’image. Pour une DLL, le point d’entrée par défaut est `DllMainCRTStartup` . Pour un EXE, il s’agit de `WinMainCRTStartup` . Vous pouvez remplacer la valeur par défaut avec l’option de l’éditeur de liens/ENTRY. Le CRT fournit une implémentation pour `DllMainCRTStartup` , `WinMainCRTStartup` et `wWinMainCRTStartup` (le point d’entrée Unicode pour un exe). Ces points d’entrée fournis par le CRT appellent des constructeurs sur des objets globaux et initialisent d’autres structures de données utilisées par certaines fonctions CRT. Ce code de démarrage ajoute environ 25 Ko à votre image s’il est lié de manière statique. S’il est lié dynamiquement, la plus grande partie du code se trouve dans la DLL, de sorte que la taille de votre image reste faible.

Pour plus d’informations, consultez la rubrique [/entry (symbole de point d’entrée)](../build/reference/entry-entry-point-symbol.md)de l’éditeur de liens.

## <a name="optimization-options"></a>Options d’optimisation

L’utilisation de l’option de l’éditeur de liens/OPT : NOWIN98 peut réduire davantage le contrôle ATL par défaut de 10 Ko, au détriment de l’augmentation du temps de chargement sur les systèmes Windows 98. Pour plus d’informations sur les options de liaison, consultez [/OPT (optimisations)](../build/reference/opt-optimizations.md).

## <a name="see-also"></a>Voir aussi

[Programmation avec des Run-Time du code ATL et C](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[DLL et comportement de la bibliothèque runtime Visual C++](../build/run-time-library-behavior.md)
