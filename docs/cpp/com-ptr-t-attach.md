---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 870e3580ed23ce994d832f7c59b951680d725e41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180496"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Section spécifique de Microsoft**

Encapsule un pointeur d'interface brut du type de ce pointeur intelligent.

## <a name="syntax"></a>Syntaxe

```
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Paramètres

*pInterface*<br/>
Pointeur d'interface brut.

*fAddRef*<br/>
Si la valeur est TRUE, `AddRef` est appelée. Si la valeur est FALSe, l’objet `_com_ptr_t` prend possession du pointeur d’interface brut sans appeler `AddRef`.

## <a name="remarks"></a>Notes

- L' **attachement (** *pInterface* **)** `AddRef` n’est pas appelé. La propriété de l'interface est passée à cet objet `_com_ptr_t`. `Release` est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé.

- **Attach (**  *pInterface* **,**  *fAddRef*  **)** Si *fAddRef* a la valeur TRUE, `AddRef` est appelé pour incrémenter le décompte de références pour le pointeur d’interface encapsulé. Si *fAddRef* a la valeur false, cet objet `_com_ptr_t` prend possession du pointeur d’interface brut sans appeler `AddRef`. `Release` est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)
