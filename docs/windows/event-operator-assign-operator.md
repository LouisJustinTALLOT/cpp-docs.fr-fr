---
title: Event::operator =, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: d8fe9820-8856-4899-9553-56226bdc4945
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a523d6ba8679bf7d0bdf98563b86946e16e7bfca
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571296"
---
# <a name="eventoperator-operator"></a>Event::operator=, opérateur
Assigne le texte spécifié **événement** référence à le **événement** instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW Event& operator=(  
   _Inout_ Event&& h  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *h*  
 Une référence rvalue à un **événement** instance.  
  
## <a name="return-value"></a>Valeur de retour  
 Un pointeur vers l’actuel **événement** instance.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Event, classe (bibliothèque de modèles Windows Runtime C++)](../windows/event-class-windows-runtime-cpp-template-library.md)