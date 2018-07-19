---
title: _com_ptr_t::Attach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8e982ebd9a09d4dfcb5e4b5e150b42a1e8d5c75
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37943795"
---
# <a name="comptrtattach"></a>_com_ptr_t::Attach
**Section spécifique à Microsoft**  
  
 Encapsule un pointeur d'interface brut du type de ce pointeur intelligent.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
void Attach( Interface* pInterface ) throw( );  
void Attach( Interface* pInterface, bool fAddRef ) throw( );  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pInterface*  
 Pointeur d'interface brut.  
  
 *fAddRef*  
 Si elle est TRUE, puis `AddRef` est appelée. Si le résultat est FALSE, le `_com_ptr_t` objet prend possession du pointeur d’interface brut sans appeler `AddRef`.  
  
## <a name="remarks"></a>Notes  
  
-   **Attacher (***pInterface***)** `AddRef` n’est pas appelée.     La propriété de l'interface est passée à cet objet `_com_ptr_t`. `Release` est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé.  
  
-   **Attacher (***pInterface* **,***fAddRef***)** si *fAddRef* a la valeur TRUE, `AddRef`est appelé pour incrémenter le décompte de références pour le pointeur d’interface encapsulé.       Si *fAddRef* est FALSE, cela `_com_ptr_t` objet prend possession du pointeur d’interface brut sans appeler `AddRef`. `Release` est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_ptr_t, classe](../cpp/com-ptr-t-class.md)