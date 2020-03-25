---
title: interior_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- stdcli::language::interior_ptr
- interior_ptr_cpp
- interior_ptr
helpviewer_keywords:
- interior_ptr keyword [C++]
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
ms.openlocfilehash: 264ac0a56996b0dcbeeb64246623eca1a3fc73ff
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172150"
---
# <a name="interior_ptr-ccli"></a>interior_ptr (C++/CLI)

Un *pointeur intérieur* déclare un pointeur vers un type référence, mais pas vers l’objet lui-même. Un pointeur intérieur peut pointer vers un descripteur de référence, un descripteur de type valeur ou boxed, un membre d’un type managé ou un élément d’un groupe managé.

## <a name="all-runtimes"></a>Tous les runtimes

(Aucune remarque pour cette fonctionnalité de langage ne s’applique à tous les runtimes.)

## <a name="windows-runtime"></a>Windows Runtime

(Aucune note de cette fonctionnalité de langage ne s’applique qu’au Windows Runtime.)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

L’exemple de syntaxe suivant montre un pointeur intérieur.

### <a name="syntax"></a>Syntaxe

```cpp
cli::interior_ptr<cv_qualifier type> var = &initializer;
```

### <a name="parameters"></a>Paramètres

*cv_qualifier*<br/>
Qualificateurs **const** ou **volatile**.

*type*<br/>
Type d’*initialiseur*.

*var*<br/>
Nom de la variable **interior_ptr**.

*initializer*<br/>
Membre d’un type référence, d’un élément ou d’un groupe managé, ou de tout autre type d’objet qu’il est possible d’assigner à un pointeur natif.

### <a name="remarks"></a>Notes

Un pointeur natif n’est pas en mesure d’effectuer le suivi d’un élément étant donné que son emplacement change dans le tas managé, ce qui entraîne le déplacement des instances d’un objet par le récupérateur de mémoire. Pour qu’un pointeur fasse correctement référence à l’instance, le runtime doit mettre à jour le pointeur sur l’objet qui vient d’être positionné.

Un **interior_ptr** représente un surensemble de la fonctionnalité d’un pointeur natif.  Par conséquent, tout ce qui peut être assigné à un pointeur natif peut aussi être assigné à un **interior_ptr**.  Un pointeur intérieur est autorisé à effectuer le même ensemble d’opérations que des pointeurs natifs, y compris la comparaison et l’arithmétique de pointeur.

Un pointeur intérieur peut uniquement être déclaré sur la pile.  Un pointeur intérieur ne peut pas être déclaré en tant que membre d’une classe.

Dans la mesure où il existe des pointeurs intérieurs uniquement sur la pile, prendre l’adresse d’un pointeur intérieur génère un pointeur non managé.

**interior_ptr** a une conversion implicite en **bool**, ce qui permet son utilisation dans les instructions conditionnelles.

Pour plus d’informations sur la façon de déclarer un pointeur intérieur qui pointe vers un objet qui ne peut pas être déplacé sur le tas récupéré par le récupérateur de mémoire, consultez [pin_ptr](pin-ptr-cpp-cli.md).

**interior_ptr** est dans l’espace de noms CLI.  Consultez [Plateforme, valeurs par défaut et espaces de noms CLI](platform-default-and-cli-namespaces-cpp-component-extensions.md) pour plus d’informations.

Pour plus d’informations sur les pointeurs intérieurs, consultez

- [Guide pratique pour déclarer et utiliser des pointeurs intérieurs et des tableaux managés (C++-CLI)](how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)

- [Guide pratique pour déclarer des types de valeur avec le mot clé interior_ptr (C++-CLI)](how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)

- [Guide pratique pour surcharger des fonctions avec des pointeurs intérieurs et des pointeurs natifs (C++-CLI)](how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)

- [Guide pratique pour déclarer des pointeurs intérieurs avec le mot clé const (C++-CLI)](how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple suivant montre comment déclarer et utiliser un pointeur intérieur dans un type référence.

```cpp
// interior_ptr.cpp
// compile with: /clr
using namespace System;

ref class MyClass {
public:
   int data;
};

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;
   h_MyClass->data = 1;
   Console::WriteLine(h_MyClass->data);

   interior_ptr<int> p = &(h_MyClass->data);
   *p = 2;
   Console::WriteLine(h_MyClass->data);

   // alternatively
   interior_ptr<MyClass ^> p2 = &h_MyClass;
   (*p2)->data = 3;
   Console::WriteLine((*p2)->data);
}
```

```Output
1
2
3
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)
