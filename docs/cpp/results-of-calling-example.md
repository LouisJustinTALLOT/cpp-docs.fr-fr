---
description: 'En savoir plus sur : résultats de l’appel de l’exemple'
title: Exemple de résultats de l'appel
ms.date: 11/19/2018
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
ms.openlocfilehash: 91da3182742414dc4850013463b74ae36aa782c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262917"
---
# <a name="results-of-calling-example"></a>Exemple de résultats de l'appel

**Spécifique à Microsoft**

## <a name="__cdecl"></a>__cdecl

Le nom de fonction décoré C est `_MyFunc` .

![Convention d’appel CDECL](../cpp/media/vc37i01.gif "Convention d'appel CDECL") <br/>
**`__cdecl`** Convention d’appel

## <a name="__stdcall-and-thiscall"></a>__stdcall et thiscall

Le nom décoré C ( **`__stdcall`** ) est `_MyFunc@20` . Le nom décoré C++ est spécifique à l’implémentation.

![ Conventions d’appel&#95;&#95;stdcall et thiscall](../cpp/media/vc37i02.gif "Conventions d’appel &#95;&#95;stdcall et thiscall") <br/>
Conventions d'appel __stdcall et thiscall

## <a name="__fastcall"></a>__fastcall

Le nom décoré C ( **`__fastcall`** ) est `@MyFunc@20` . Le nom décoré C++ est spécifique à l’implémentation.

![Convention d’appel pour &#95;&#95;fastcall](../cpp/media/vc37i03.gif "Convention d’appel pour &#95;&#95;fastcall") <br/>
Convention d’appel __fastcall

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Exemple d’appel : prototype et appel de fonction](../cpp/calling-example-function-prototype-and-call.md)
