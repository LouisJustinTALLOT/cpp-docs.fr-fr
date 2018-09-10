---
title: enable_shared_from_this, classe │ Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::enable_shared_from_this
dev_langs:
- C++
helpviewer_keywords:
- enable_shared_from_this class
- enable_shared_from_this
ms.assetid: 9237603d-22e2-421f-b070-838ac006baf5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d74db7e9c88baec8aad7f966c0af3f2ec7840f0a
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110550"
---
# <a name="enablesharedfromthis-class"></a>enable_shared_from_this, classe

Aide à générer un `shared_ptr`.

## <a name="syntax"></a>Syntaxe

```cpp
class enable_shared_from_this {
public:
    shared_ptr<Ty>
        shared_from_this();
    shared_ptr<const Ty> shared_from_this() const;
protected:
    enable_shared_from_this();
    enable_shared_from_this(const enable_shared_from_this&);
    enable_shared_from_this& operator=(const enable_shared_from_this&);
    ~enable_shared_from_this();
};
```

### <a name="parameters"></a>Paramètres

*Ty*<br/>
Type contrôlé par le pointeur partagé.

## <a name="remarks"></a>Notes

Les objets dérivés de `enable_shared_from_this` peuvent utiliser les méthodes `shared_from_this` dans des fonctions membres pour créer les propriétaires [shared_ptr](../standard-library/shared-ptr-class.md) de l’instance qui partagent la propriété avec les propriétaires `shared_ptr` existants. Sinon, si vous créez un nouveau `shared_ptr` à l’aide de **cela**, il est différent des existant `shared_ptr` propriétaires, ce qui peuvent entraîner des références non valides ou l’objet doit être supprimé plusieurs fois.

Les constructeurs, le destructeur et l’opérateur d’assignation sont protégés pour éviter toute mauvaise utilisation accidentelle. Le type d’argument de modèle *Ty* doit être du type de la classe dérivée.

Pour obtenir un exemple d’utilisation, consultez [enable_shared_from_this::shared_from_this](#shared_from_this).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<memory>

**Espace de noms :** std

## <a name="shared_from_this"></a>  enable_shared_from_this::shared_from_this

Génère un `shared_ptr` qui partage la propriété de l’instance avec les propriétaires `shared_ptr` existants.

```cpp
shared_ptr<T> shared_from_this();
shared_ptr<const T> shared_from_this() const;
```

### <a name="remarks"></a>Notes

Quand vous dérivez des objets à partir de la classe de base `enable_shared_from_this`, les fonctions membres de modèle `shared_from_this` retournent une [classe shared_ptr](../standard-library/shared-ptr-class.md) qui partage la propriété de cette instance avec les propriétaires `shared_ptr` existants. Sinon, si vous créez un nouveau `shared_ptr` de **cela**, il diffère de celui existant `shared_ptr` propriétaires, ce qui peuvent entraîner des références non valides ou l’objet doit être supprimé plusieurs fois. Le comportement est indéfini si vous appelez `shared_from_this` sur une instance qui n’est pas déjà détenue par un objet `shared_ptr`.

### <a name="example"></a>Exemple

```cpp
// std_memory_shared_from_this.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

struct base : public std::enable_shared_from_this<base>
{
    int val;
    shared_ptr<base> share_more()
    {
        return shared_from_this();
    }
};

int main()
{
    auto sp1 = make_shared<base>();
    auto sp2 = sp1->share_more();

    sp1->val = 3;
    cout << "sp2->val == " << sp2->val << endl;
    return 0;
}
```

```Output
sp2->val == 3
```

## <a name="see-also"></a>Voir aussi

[enable_shared_from_this::shared_from_this](#shared_from_this)<br/>
[shared_ptr, classe](../standard-library/shared-ptr-class.md)<br/>