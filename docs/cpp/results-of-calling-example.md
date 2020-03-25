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
ms.openlocfilehash: edbeb187e568b833673d91ef70ff57fbd460659c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179053"
---
# <a name="results-of-calling-example"></a>Exemple de résultats de l'appel

**Section spécifique de Microsoft**

## <a name="__cdecl"></a>__cdecl

Le nom de fonction décoré C est `_MyFunc`.

![Convention d’appel CDECL](../cpp/media/vc37i01.gif "Convention d'appel CDECL") <br/>
Convention d’appel **__cdecl**

## <a name="__stdcall-and-thiscall"></a>__stdcall et thiscall

Le nom décoré C ( **__stdcall**) est `_MyFunc@20`. Le C++ nom décoré est spécifique à l’implémentation.

![&#95;&#95;conventions d’appel StdCall et thiscall](../cpp/media/vc37i02.gif "&#95;&#95;conventions d’appel StdCall et thiscall") <br/>
Conventions d'appel __stdcall et thiscall

## <a name="__fastcall"></a>__fastcall

Le nom décoré C ( **__fastcall**) est `@MyFunc@20`. Le C++ nom décoré est spécifique à l’implémentation.

![Convention d’appel &#95; &#95;pour fastcall](../cpp/media/vc37i03.gif "Convention d’appel &#95; &#95;pour fastcall") <br/>
Convention d’appel __fastcall

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Exemple d’appel : prototype et appel de fonction](../cpp/calling-example-function-prototype-and-call.md)
