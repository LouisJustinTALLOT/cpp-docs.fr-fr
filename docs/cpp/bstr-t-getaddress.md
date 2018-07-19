---
title: _bstr_t::GetAddress | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetAddress
dev_langs:
- C++
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4895153abe248265e0aacfbe636b9a4bd46ed205
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941195"
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress
**Section spécifique à Microsoft**  
  
 Libère toute chaîne existante et retourne l'adresse d'une chaîne nouvellement allouée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BSTR* GetAddress( );  
  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Pointeur désignant le `BSTR` encapsulé par l'objet `_bstr_t`.  
  
## <a name="remarks"></a>Notes  
 `GetAddress` affecte tous les objets `_bstr_t` qui partagent un `BSTR`. Plusieurs `_bstr_t` peuvent partager un `BSTR` en utilisant le constructeur de copie et et **opérateur =**.  
  
## <a name="example"></a>Exemple  
 Consultez [_bstr_t::Assign](../cpp/bstr-t-assign.md) pour obtenir un exemple utilisant `GetAddress`.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_bstr_t, classe](../cpp/bstr-t-class.md)