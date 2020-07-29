---
title: pin_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
ms.openlocfilehash: 9a9144229b75c09a892ddbf5bd592e67c7c2b6d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230556"
---
# <a name="pin_ptr-ccli"></a>pin_ptr (C++/CLI)

Déclare un *pointeur épingle*, utilisé uniquement avec le common language runtime.

## <a name="all-runtimes"></a>Tous les runtimes

(Aucune remarque pour cette fonctionnalité de langage ne s’applique à tous les runtimes.)

## <a name="windows-runtime"></a>Windows Runtime

(Cette fonctionnalité de langage n’est pas prise en charge dans Windows Runtime.)

## <a name="common-language-runtime"></a>Common Language Runtime

Un *pointeur épingle* est un pointeur intérieur qui empêche l’objet pointé d’être déplacé vers le segment collecté par le Garbage Collector. Autrement dit, la valeur d’un pointeur épingle n’est pas modifiée par le common language runtime. Cela est nécessaire lorsque vous transmettez l’adresse d’une classe managée à une fonction non managée de sorte que l’adresse ne change pas de manière inattendue pendant la résolution de l’appel de fonction non managé.

### <a name="syntax"></a>Syntaxe

```cpp
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;
```

### <a name="parameters"></a>Paramètres

*cv_qualifier*<br/>
**`const`****`volatile`** qualificateurs ou. Par défaut, un pointeur épingle est **`volatile`** . Elle est redondante, mais pas une erreur pour déclarer un pointeur épingle **`volatile`** .

*type*<br/>
Type d’*initialiseur*.

*var*<br/>
Nom de la variable **pin_ptr**.

*initializer*<br/>
Membre d’un type référence, d’un élément ou d’un groupe managé, ou de tout autre type d’objet qu’il est possible d’assigner à un pointeur natif.

### <a name="remarks"></a>Notes

Un **pin_ptr** représente un surensemble de la fonctionnalité d’un pointeur natif. Par conséquent, tout ce qui peut être assigné à un pointeur natif peut aussi être assigné à un **pin_ptr**. Un pointeur intérieur est autorisé à effectuer le même ensemble d’opérations que des pointeurs natifs, y compris la comparaison et l’arithmétique de pointeur.

Un objet ou sous-objet d’une classe managée peut être épinglé, auquel cas le common language runtime n’est pas déplacé lors du nettoyage de la mémoire. Son utilisation principale consiste à passer un pointeur dans des données managées en tant que paramètre réel d’un appel de fonction non managée. Lors d’un cycle de nettoyage, le runtime inspecte les métadonnées créées pour le pointeur épingle et ne déplace les éléments auxquels il pointe.

L’épinglage d’un objet épingle également ses champs de valeur (les champs de type valeur ou primitif). Toutefois, les champs déclarés par un handle de suivi (`%`) ne sont pas épinglés.

L’épinglage d’un sous-objet défini dans un objet managé a pour effet d’épingler l’objet entier.

Si le pointeur épingle est réassigné afin de pointer vers une nouvelle valeur, l’instance précédemment pointée n’est plus considérée comme épinglée.

Un objet est uniquement épinglé tant qu’un **pin_ptr** le pointe. L’objet n’est plus épinglé lorsque son pointeur épingle n’est plus à portée ou est défini sur [nullptr](nullptr-cpp-component-extensions.md). Une fois le **pin_ptr** hors de portée, l’objet qui était épinglé peut être déplacé dans le segment par le récupérateur de mémoire. Les pointeurs natifs qui pointent toujours vers l’objet ne sont pas mis à jour, et l’annulation du référencement de l’un d’entre eux peut entraîner une exception irrécupérable.

Si aucun pointeur épingle ne pointe vers l’objet (tous sont hors de portée, ont été réassignés pour pointer vers d’autres objets ou ont été définis sur [nullptr](nullptr-cpp-component-extensions.md)), l’objet ne sera alors pas épinglé.

Un pointeur épingle peut pointer vers un handle de référence, un handle de type valeur ou boxed, un membre d’un type managé ou un élément d’un groupe managé. Il ne peut pas pointer vers un type référence.

En prenant l’adresse d’un **pin_ptr** qui pointe vers un objet natif, vous pourriez entraîner un comportement indéfini.

Les pointeurs épingles ne peuvent être déclarés en tant que variables locales non statiques sur la pile.

Ils ne peuvent être utilisés en tant que :

- paramètres de fonction

- type de retour d’une fonction

- membre d’une classe

- type de cible d’un cast.

**pin_ptr** se trouve dans l’espace de noms `cli`. Consultez [Plateforme, valeur par défaut et espaces de noms cli](platform-default-and-cli-namespaces-cpp-component-extensions.md) pour plus d’informations.

Consultez [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md) pour plus d’informations sur les pointeurs intérieurs.

Pour plus d’informations sur les pointeurs épinglés, consultez Guide pratique [pour épingler des pointeurs et des tableaux](how-to-pin-pointers-and-arrays.md) et [Comment : déclarer des pointeurs épinglés et des types valeur](how-to-declare-pinning-pointers-and-value-types.md).

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple suivant utilise **pin_ptr** pour contraindre la position du premier élément d’un tableau.

```cpp
// pin_ptr_1.cpp
// compile with: /clr
using namespace System;
#define SIZE 10

#pragma unmanaged
// native function that initializes an array
void native_function(int* p) {
   for(int i = 0 ; i < 10 ; i++)
    p[i] = i;
}
#pragma managed

public ref class A {
private:
   array<int>^ arr;   // CLR integer array

public:
   A() {
      arr = gcnew array<int>(SIZE);
   }

   void load() {
   pin_ptr<int> p = &arr[0];   // pin pointer to first element in arr
   int* np = p;   // pointer to the first element in arr
   native_function(np);   // pass pointer to native function
   }

   int sum() {
      int total = 0;
      for (int i = 0 ; i < SIZE ; i++)
         total += arr[i];
      return total;
   }
};

int main() {
   A^ a = gcnew A;
   a->load();   // initialize managed array using the native function
   Console::WriteLine(a->sum());
}
```

```Output
45
```

L’exemple suivant montre qu’un pointeur intérieur peut être converti en un pointeur épingle, et que le type de retour de l’opérateur address-of (`&`) est un pointeur intérieur lorsque l’opérande est sur le segment managé.

```cpp
// pin_ptr_2.cpp
// compile with: /clr
using namespace System;

ref struct G {
   G() : i(1) {}
   int i;
};

ref struct H {
   H() : j(2) {}
   int j;
};

int main() {
   G ^ g = gcnew G;   // g is a whole reference object pointer
   H ^ h = gcnew H;

   interior_ptr<int> l = &(g->i);   // l is interior pointer

   pin_ptr<int> k = &(h->j);   // k is a pinning interior pointer

   k = l;   // ok
   Console::WriteLine(*k);
};
```

```Output
1
```

L’exemple suivant montre qu’un pointeur épingle peut être converti en un autre type.

```cpp
// pin_ptr_3.cpp
// compile with: /clr
using namespace System;

ref class ManagedType {
public:
   int i;
};

int main() {
   ManagedType ^mt = gcnew ManagedType;
   pin_ptr<int> pt = &mt->i;
   *pt = 8;
   Console::WriteLine(mt->i);

   char *pc = ( char* ) pt;
   *pc = 255;
   Console::WriteLine(mt->i);
}
```

```Output
8
255
```
