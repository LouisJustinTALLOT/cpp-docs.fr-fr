---
title: Compilateur avertissement (niveau 1) C4730 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4730
dev_langs: C++
helpviewer_keywords: C4730
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 334c53b030097dc822451b0e555a51c90e70d904
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4730"></a>Avertissement du compilateur (niveau 1) C4730
'main' : combinaison de _m64 et d’expressions peuvent entraîner un code erroné de virgule flottante  
  
 Une fonction utilise [__m64](../../cpp/m64.md) et **float**/**double** types. Espace de Registre, car les intrinsèques MMX et registres en virgule flottante partagent le même physique (ne peut pas être utilisés simultanément), à l’aide de `__m64` et **float**/**double** types dans le même fonction peut entraîner une altération des données et peut provoquer une exception.  
  
 À utiliser en toute sécurité `__m64` types et les types à virgule flottante dans la même fonction, chaque instruction qui utilise un des types doit être séparée par le **_m_empty()** (pour MMX) ou **_m_femms()** (pour 3DNow !) intrinsèques.  
  
 L’exemple suivant génère l’erreur C4730 :  
  
```  
// C4730.cpp  
// compile with: /W1  
// processor: x86  
#include "mmintrin.h"  
  
void func(double)  
{  
}  
  
int main(__m64 a, __m64 b)  
{  
   __m64 m;  
   double f;  
   f = 1.0;  
   m = _m_paddb(a, b);  
   // uncomment the next line to resolve C4730  
   // _m_empty();  
   func(f * 3.0);   // C4730  
}  
```