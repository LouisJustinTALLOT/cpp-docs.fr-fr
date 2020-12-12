---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4435'
title: Avertissement du compilateur (niveau 4) C4435
ms.date: 11/04/2016
f1_keywords:
- C4435
helpviewer_keywords:
- C4435
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
ms.openlocfilehash: ce5ee4e32f6efa1e7986d55fafa0ceec8b754351
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203508"
---
# <a name="compiler-warning-level-4-c4435"></a>Avertissement du compilateur (niveau 4) C4435

'classe1' : la disposition des objets sous /vd2 sera modifiée en raison de la base virtuelle 'classe2'

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

Sous l’option de compilation par défaut de/VD1, la classe dérivée n’a pas de `vtordisp` champ pour la base virtuelle indiquée.  Si/VD2 ou `#pragma vtordisp(2)` est activé, un `vtordisp` champ est présent, ce qui modifie la disposition de l’objet.  Cela peut entraîner des problèmes de compatibilité binaire si les modules d’interaction sont compilés avec des `vtordisp` paramètres différents.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4435.

```cpp
// C4435.cpp
// compile with: /c /W4
#pragma warning(default : 4435)
class A
{
public:
    virtual ~A() {}
};

class B : public virtual A  // C4435
{};
```

## <a name="see-also"></a>Voir aussi

[vtordisp](../../preprocessor/vtordisp.md)<br/>
[/VD (désactiver les déplacements de construction)](../../build/reference/vd-disable-construction-displacements.md)
