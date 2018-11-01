---
title: Avertissement du compilateur (niveau 4) C4435
ms.date: 11/04/2016
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
ms.openlocfilehash: 7db1d483f571289c5b890c223ba1e59ba3d1f41e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572326"
---
# <a name="compiler-warning-level-4-c4435"></a>Avertissement du compilateur (niveau 4) C4435

'classe1' : la disposition des objets sous /vd2 sera modifiée en raison de la base virtuelle 'classe2'

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

Sous la valeur par défaut l’option de/vd1 de compilation, la classe dérivée n’a pas un `vtordisp` champ pour la base virtuelle indiquée.  Si/vd2 ou `#pragma vtordisp(2)` est en effet, un `vtordisp` champ seront présent, modification de la disposition de l’objet.  Cela peut entraîner des problèmes de compatibilité binaire si l’interaction des modules sont compilés avec différents `vtordisp` paramètres.

## <a name="example"></a>Exemple

L’exemple suivant génère C4435.

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
[/vd (Désactiver les déplacements de construction)](../../build/reference/vd-disable-construction-displacements.md)