---
title: logic_error, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- stdexcept/std::logic_error
dev_langs:
- C++
helpviewer_keywords:
- logic_error class
ms.assetid: b290d73d-94e1-4288-af86-2bb5d71f677a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc6d3e2ec67cc60e099016ac3d7cf4d213322ce2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33851994"
---
# <a name="logicerror-class"></a>logic_error, classe

Classe qui sert de classe de base pour toutes les exceptions levées pour signaler des erreurs normalement détectables avant l'exécution du programme, telles que les violations de conditions préalables logiques.

## <a name="syntax"></a>Syntaxe

```cpp
class logic_error : public exception {
public:
    explicit logic_error(const string& message);

    explicit logic_error(const char *message);

};
```

## <a name="remarks"></a>Notes

La valeur retournée par [what](../standard-library/exception-class.md) est une copie de **message**`.`[data](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Exemple

```cpp
// logic_error.cpp
// compile with: /EHsc /GR
#include <iostream>
using namespace std;

int main( )
{
   try
   {
      throw logic_error( "logic error" );
   }
   catch ( exception &e )
   {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
```

```Output
Caught: logic error
Type: class std::logic_error
```

## <a name="requirements"></a>Spécifications

**En-tête :** \<stdexcept>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[exception, classe](../standard-library/exception-class.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
