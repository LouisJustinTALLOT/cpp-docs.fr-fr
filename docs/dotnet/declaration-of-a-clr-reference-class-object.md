---
title: Déclaration d’un objet de classe de référence CLR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- types [C++], reference types
- reference types, CLR
ms.assetid: 6d64f746-3715-4948-ada3-88859f4150e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f3e8ec6407e12d0c26331d45dc1659277feed016
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444578"
---
# <a name="declaration-of-a-clr-reference-class-object"></a>Déclaration d'un objet de classe de référence du CLR

La syntaxe permettant de déclarer et instancier un objet d’un type de classe de référence a changé d’Extensions managées pour C++ vers Visual C++.

Dans les Extensions managées, un objet de type de classe de référence est déclaré à l’aide de la syntaxe de pointeur ISO-C++, avec la possibilité d’utiliser le `__gc` mot clé à gauche de l’étoile (`*`). Par exemple, voici une variété de référence de déclarations d’objet de type classe sous la syntaxe des Extensions managées :

```
public __gc class Form1 : public System::Windows::Forms::Form {
private:
   System::ComponentModel::Container __gc *components;
   Button __gc *button1;
   DataGrid __gc *myDataGrid;
   DataSet __gc *myDataSet;

   void PrintValues( Array* myArr ) {
      System::Collections::IEnumerator* myEnumerator =
         myArr->GetEnumerator();

      Array *localArray;
      myArr->Copy(myArr, localArray, myArr->Length);
   }
};
```

Dans la nouvelle syntaxe, vous déclarez un objet de type de classe de référence à l’aide d’un nouveau jeton déclaratif (`^`) appelé formellement une *handle de suivi* et de manière plus informelle, comme un *hat*. (L’adjectif suivi signifie qu’un type référence se trouve dans le tas CLR et peut par conséquent changer d’emplacement de façon transparente pendant le compactage du tas de garbage collection. Un handle de suivi est mis à jour en toute transparence pendant l’exécution. Deux concepts similaires sont la *référence de suivi* (`%`) et le *pointeur intérieur* (`interior_ptr<>`), nous l’avons vu dans [sémantique de Type valeur](../dotnet/value-type-semantics.md).

Les raisons principales pour la syntaxe déclarative en dehors d’une réutilisation de la syntaxe de pointeur ISO-C++ sont les suivantes :

- L’utilisation de la syntaxe de pointeur ne permettaient pas les opérateurs surchargés à appliquer directement à un objet de référence. Au lieu de cela, il fallait appeler l’opérateur à l’aide de son nom interne, tel que `rV1->op_Addition(rV2)` au lieu de la plus intuitive `rV1+rV2`.

- Un nombre d’opérations de pointeur, telles que la conversion et l’arithmétique, ne pas autorisé pour les objets stockés dans un garbage collectés du tas. La notion de handle de suivi une meilleure capture la nature d’un type de référence CLR.

Le `__gc` modificateur sur un handle de suivi n’est pas nécessaire et n’est pas pris en charge. L’utilisation de l’objet lui-même n’est pas modifiée. elle accède toujours aux membres via l’opérateur de sélection de membre de pointeur (`->`). Par exemple, voici l’exemple de code Extensions managées précédent traduit dans la nouvelle syntaxe :

```
public ref class Form1: public System::Windows::Forms::Form {
private:
   System::ComponentModel::Container^ components;
   Button^ button1;
   DataGrid^ myDataGrid;
   DataSet^ myDataSet;

   void PrintValues( Array^ myArr ) {
      System::Collections::IEnumerator^ myEnumerator =
         myArr->GetEnumerator();

      Array ^localArray;
      myArr->Copy(myArr, localArray, myArr->Length);   }
};
```

## <a name="dynamic-allocation-of-an-object-on-the-clr-heap"></a>Allocation dynamique d’un objet sur le tas CLR

Dans les Extensions managées, l’existence de deux `new` expressions à allouer entre le tas natif et managé a été largement transparent. Dans presque tous les cas, le compilateur est en mesure d’utiliser le contexte pour déterminer s’il faut allouer de la mémoire à partir du tas natif ou managé. Par exemple :

```
Button *button1 = new Button; // OK: managed heap
int *pi1 = new int;           // OK: native heap
Int32 *pi2 = new Int32;       // OK: managed heap
```

Lorsque vous ne souhaitez pas l’allocation de tas contextuelle, vous pouvez diriger le compilateur avec soit le `__gc` ou `__nogc` mot clé. Dans la nouvelle syntaxe, la nature distincte des deux nouvelles expressions est rendue explicite avec l’introduction de la `gcnew` mot clé. Par exemple, les trois déclarations précédentes se présenter comme suit dans la nouvelle syntaxe :

```
Button^ button1 = gcnew Button;        // OK: managed heap
int * pi1 = new int;                   // OK: native heap
Int32^ pi2 = gcnew Int32; // OK: managed heap
```

Voici l’initialisation des Extensions managées de le `Form1` membres déclarés dans la section précédente :

```
void InitializeComponent() {
   components = new System::ComponentModel::Container();
   button1 = new System::Windows::Forms::Button();
   myDataGrid = new DataGrid();

   button1->Click +=
      new System::EventHandler(this, &Form1::button1_Click);
}
```

Voici la même initialisation remodelée vers la nouvelle syntaxe. Notez que le chapeau n’est pas requis pour le type de référence lorsqu’il est la cible d’un `gcnew` expression.

```
void InitializeComponent() {
   components = gcnew System::ComponentModel::Container;
   button1 = gcnew System::Windows::Forms::Button;
   myDataGrid = gcnew DataGrid;

   button1->Click +=
      gcnew System::EventHandler( this, &Form1::button1_Click );
}
```

## <a name="a-tracking-reference-to-no-object"></a>Une référence de suivi à aucun objet

Dans la nouvelle syntaxe, `0` ne représente plus une adresse nulle mais est traité comme un entier, de même que `1`, `10`, ou `100`. Un nouveau jeton spécial représente une valeur null pour une référence de suivi. Par exemple, dans les Extensions managées, nous initialiser un type de référence pour ne répondre à aucun objet comme suit :

```
// OK: we set obj to refer to no object
Object * obj = 0;

// Error: no implicit boxing
Object * obj2 = 1;
```

Dans la nouvelle syntaxe, toute initialisation ou assignation d’une valeur de type à un `Object` entraîne la conversion boxing implicit de ce type de valeur. Dans la nouvelle syntaxe, les deux `obj` et `obj2` sont initialisés en objets Int32 boxed les valeurs 0 et 1, respectivement. Exemple :

```
// causes the implicit boxing of both 0 and 1
Object ^ obj = 0;
Object ^ obj2 = 1;
```

Par conséquent, pour effectuer l’initialisation explicite, affectation et la comparaison d’un handle de suivi vers null, utilisez un nouveau mot clé, `nullptr`.  La révision correcte de l’exemple d’origine se présente comme suit :

```
// OK: we set obj to refer to no object
Object ^ obj = nullptr;

// OK: we initialize obj2 to a Int32^
Object ^ obj2 = 1;
```

Cela complique quelque peu le portage du code existant dans la nouvelle syntaxe. Par exemple, considérez la déclaration de classe de valeur suivantes :

```
__value struct Holder {
   Holder( Continuation* c, Sexpr* v ) {
      cont = c;
      value = v;
      args = 0;
      env = 0;
   }

private:
   Continuation* cont;
   Sexpr * value;
   Environment* env;
   Sexpr * args __gc [];
};
```

Ici, les deux `args` et `env` sont des types de référence CLR. L’initialisation de ces deux membres à `0` dans le constructeur ne peut pas rester inchangée dans la transition vers la nouvelle syntaxe. Au lieu de cela, ils doivent être remplacées par `nullptr`:

```
value struct Holder {
   Holder( Continuation^ c, Sexpr^ v )
   {
      cont = c;
      value = v;
      args = nullptr;
      env = nullptr;
   }

private:
   Continuation^ cont;
   Sexpr^ value;
   Environment^ env;
   array<Sexpr^>^ args;
};
```

De même, les tests par rapport à ces membres en les comparant à `0` doit également être modifié pour comparer des membres à `nullptr`. Voici la syntaxe des Extensions managées :

```
Sexpr * Loop (Sexpr* input) {
   value = 0;
   Holder holder = Interpret(this, input, env);

   while (holder.cont != 0) {
      if (holder.env != 0) {
         holder=Interpret(holder.cont,holder.value,holder.env);
      }
      else if (holder.args != 0) {
         holder =
         holder.value->closure()->
         apply(holder.cont,holder.args);
      }
   }

   return value;
}
```

Voici la révision, en remplaçant chaque `0` instance avec un `nullptr`. L’outil de traduction permet cette transformation en automatisant de nombreuses pas toutes les occurrences, y compris l’aide de la `NULL` (macro).

```
Sexpr ^ Loop (Sexpr^ input) {
   value = nullptr;
   Holder holder = Interpret(this, input, env);

   while ( holder.cont != nullptr ) {
      if ( holder.env != nullptr ) {
         holder=Interpret(holder.cont,holder.value,holder.env);
      }
      else if (holder.args != nullptr ) {
         holder =
         holder.value->closure()->
         apply(holder.cont,holder.args);
      }
   }

   return value;
}
```

Le `nullptr` est converti en un type de handle de pointeur ou de suivi, mais n’est pas promue en un type intégral. Par exemple, dans le jeu suivant d’initialisations, le `nullptr` est valide uniquement en tant qu’une valeur initiale pour les deux premières.

```
// OK: we set obj and pstr to refer to no object
Object^ obj = nullptr;
char*   pstr = nullptr; // 0 would also work here

// Error: no conversion of nullptr to 0
int ival = nullptr;
```

De même, étant donné un jeu surchargé de méthodes telles que les éléments suivants :

```
void f( Object^ ); // (1)
void f( char* );   // (2)
void f( int );     // (3)
```

Un appel avec un `nullptr` littéral, comme suit :

```
// Error: ambiguous: matches (1) and (2)
f(  nullptr );
```

est ambigu, car le `nullptr` correspond à un handle de suivi et un pointeur et il n’existe aucune préférence donnée à un type plutôt que l’autre. (Cette situation nécessite un cast explicite pour lever l’ambiguïté).

Un appel avec un `0` exactement correspond à l’instance (3) :

```
// OK: matches (3)
f( 0 );
```

Étant donné que `0` est de type entier. Ont été `f(int)` absent, l’appel sans ambiguïté associerait `f(char*)` via une conversion standard. Les règles de correspondance accorder la priorité d’une correspondance exacte sur une conversion standard. En l’absence d’une correspondance exacte, une conversion standard est prioritaire sur la conversion boxing implicite d’un type valeur. C’est pourquoi il n’existe aucune ambiguïté.

## <a name="see-also"></a>Voir aussi

[Types managés (C++ / c++ / CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[Classes et structs](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[Handle de l’opérateur Object (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)<br/>
[nullptr](../windows/nullptr-cpp-component-extensions.md)