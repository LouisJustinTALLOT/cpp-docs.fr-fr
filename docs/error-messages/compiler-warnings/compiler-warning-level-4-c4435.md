---
title: Compilateur avertissement (niveau 4) C4435 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c9a69e0d899e1a79c1d91b7c18c0eacaf66d32a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027295"
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