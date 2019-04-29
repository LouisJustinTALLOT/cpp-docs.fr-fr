---
title: Exemple de résultats de l'appel
ms.date: 11/19/2018
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
ms.openlocfilehash: dcd1f9002362b7726883c6ce4f74fda9ab593544
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268050"
---
# <a name="results-of-calling-example"></a>Exemple de résultats de l'appel

**Section spécifique à Microsoft**

## <a name="cdecl"></a>__cdecl

Le nom de fonction décoré C est `_MyFunc`.

![Convention d’appel CDECL](../cpp/media/vc37i01.gif "convention d’appel CDECL") <br/>
Le **__cdecl** convention d’appel

## <a name="stdcall-and-thiscall"></a>__stdcall et thiscall

Le nom décoré C (**__stdcall**) est `_MyFunc@20`. Le nom décoré C++ est spécifique à l’implémentation.

![&#95;&#95;STDCALL et conventions d’appel thiscall](../cpp/media/vc37i02.gif "&#95;&#95;stdcall et conventions d’appel thiscall") <br/>
Conventions d'appel __stdcall et thiscall

## <a name="fastcall"></a>__fastcall

Le nom décoré C (**__fastcall**) est `@MyFunc@20`. Le nom décoré C++ est spécifique à l’implémentation.

![Convention pour l’appel &#95; &#95;fastcall](../cpp/media/vc37i03.gif "appelant convention pour &#95; &#95;fastcall") <br/>
Convention d’appel __fastcall

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Exemple d’appel : prototype et appel de fonction](../cpp/calling-example-function-prototype-and-call.md)