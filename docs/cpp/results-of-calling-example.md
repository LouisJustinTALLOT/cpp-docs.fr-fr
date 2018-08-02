---
title: Résultats de l’exemple d’appel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 9c49457aecb93b16ffb294f88e4f6643826492e2
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465690"
---
# <a name="results-of-calling-example"></a>Exemple de résultats de l'appel
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
  
## <a name="cdecl"></a>__cdecl  
 Le nom de fonction décoré C est « _MyFunc ».  
  
 ![Convention d’appel CDECL](../cpp/media/vc37i01.gif "vc37I01")  
Le **__cdecl** convention d’appel  
  
## <a name="stdcall-and-thiscall"></a>__stdcall et thiscall  
 Le nom décoré C (**__stdcall**) est «_MyFunc@20. » Le nom décoré C++ est propriétaire.  
  
 ![&#95;&#95;STDCALL et conventions d’appel thiscall](../cpp/media/vc37i02.gif "vc37I02")  
Conventions d’appel __stdcall et thiscall  
  
## <a name="fastcall"></a>__fastcall  
 Le nom décoré C (**__fastcall**) est «@MyFunc@20. » Le nom décoré C++ est propriétaire.  
  
 ![Convention pour l’appel &#95; &#95;fastcall](../cpp/media/vc37i03.gif "vc37I03")  
Convention d’appel __fastcall  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple d’appel : prototype et appel de fonction](../cpp/calling-example-function-prototype-and-call.md)