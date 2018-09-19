---
title: Résultats de l’exemple d’appel | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8f09109aab5823f339de76a1337eea77a0794cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037747"
---
# <a name="results-of-calling-example"></a>Exemple de résultats de l'appel

**Section spécifique à Microsoft**

## <a name="cdecl"></a>__cdecl

Le nom de fonction décoré C est `_MyFunc`.

![Convention d’appel CDECL](../cpp/media/vc37i01.gif "vc37I01") le **__cdecl** convention d’appel

## <a name="stdcall-and-thiscall"></a>__stdcall et thiscall

Le nom décoré C (**__stdcall**) est `_MyFunc@20`. Le nom décoré C++ est spécifique à l’implémentation.

![&#95;&#95;STDCALL et conventions d’appel thiscall](../cpp/media/vc37i02.gif "vc37I02") __stdcall et thiscall conventions d’appel

## <a name="fastcall"></a>__fastcall

Le nom décoré C (**__fastcall**) est `@MyFunc@20`. Le nom décoré C++ est spécifique à l’implémentation.

![Convention pour l’appel &#95; &#95;fastcall](../cpp/media/vc37i03.gif "vc37I03") la convention d’appel __fastcall

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Exemple d’appel : prototype et appel de fonction](../cpp/calling-example-function-prototype-and-call.md)