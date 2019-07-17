---
title: bad_weak_ptr, classe
ms.date: 11/04/2016
f1_keywords:
- memory/std::bad_weak_ptr
helpviewer_keywords:
- bad_weak_ptr
- bad_weak_ptr class
ms.assetid: a09336d5-7237-4480-ab6b-3787e0e6025e
ms.openlocfilehash: 8ea29f12a8a86bd6b58c5051645182d69ff43389
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246185"
---
# <a name="badweakptr-class"></a>bad_weak_ptr, classe

Signale une exception weak_ptr incorrecte.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_weak_ptr : public std::exception
{
    bad_weak_ptr();
    const char *what() throw();
};
```

## <a name="remarks"></a>Notes

La classe décrit une exception qui peut être levée à partir du constructeur de [classe shared_ptr](../standard-library/shared-ptr-class.md) qui accepte un argument de type [classe weak_ptr](../standard-library/weak-ptr-class.md). La fonction membre `what` retourne `"bad_weak_ptr"`.

## <a name="example"></a>Exemples

```cpp
// std__memory__bad_weak_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int);
        wp = sp;
    }

    try
    {
        std::shared_ptr<int> sp1(wp); // weak_ptr has expired
    }
    catch (const std::bad_weak_ptr&)
    {
        std::cout << "bad weak pointer" << std::endl;
    }
    catch (...)
    {
        std::cout << "unknown exception" << std::endl;
    }

    return (0);
}
```

```Output
bad weak pointer
```

## <a name="see-also"></a>Voir aussi

[weak_ptr, classe](../standard-library/weak-ptr-class.md)<br/>
