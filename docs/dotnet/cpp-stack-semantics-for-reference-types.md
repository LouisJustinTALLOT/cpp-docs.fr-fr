---
description: 'En savoir plus sur : sémantique de pile C++ pour les types référence'
title: Sémantique de pile C++ pour les types de référence
ms.date: 11/04/2016
helpviewer_keywords:
- reference types, C++ stack semantics for
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
ms.openlocfilehash: a7f377225e70eff4093d4b9820a3d14644b96f58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124317"
---
# <a name="c-stack-semantics-for-reference-types"></a>Sémantique de pile C++ pour les types de référence

Avant Visual Studio 2005, une instance d’un type de référence pouvait uniquement être créée à l’aide de l' **`new`** opérateur, qui a créé l’objet sur le tas récupéré par le garbage collector. Toutefois, vous pouvez à présent créer une instance d'un type de référence en utilisant la même syntaxe que vous devriez utiliser pour créer une instance d'un type natif dans la pile. Vous n’avez donc pas besoin d’utiliser [ref New, gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md) pour créer un objet d’un type référence. Et lorsque l'objet est hors de portée, le compilateur appelle le destructeur de l'objet.

## <a name="remarks"></a>Notes

Quand vous créez une instance d’un type référence à l’aide de la sémantique de pile, le compilateur crée en interne l’instance sur le tas récupéré par le garbage collector (à l’aide de **`gcnew`** ).

Lorsque la signature ou le type de retour d'une fonction inclut une instance d'un type de référence par valeur, la fonction est marquée dans les métadonnées comme nécessitant une gestion spéciale (avec modreq). Cette gestion spéciale est actuellement fournie par les clients Visual C++ ; les autres langues ne prennent pas en charge les fonctions "gourmandes" ou les données qui utilisent les types de référence créés avec la sémantique de pile.

L’une des raisons d’utiliser **`gcnew`** (allocation dynamique) au lieu de la sémantique de pile serait si le type n’a pas de destructeur. En outre, l'utilisation de types de référence créés avec la sémantique de pile dans les signatures de fonction ne serait pas possible si vous souhaitez que vos fonctions soient utilisées dans des langages autres que Visual C++.

Le compilateur ne génère pas de constructeur de copies pour un type de référence. Par conséquent, si vous définissez une fonction qui utilise un type de référence pour chaque valeur dans la signature, vous devez définir un constructeur de copie pour le type de référence. Un constructeur de copie pour un type de référence possède une signature au format suivant : `R(R%){}`.

Le compilateur ne génère pas d'opérateur d'affectation par défaut pour un type de référence. Un opérateur d'affectation vous permet de créer un objet avec la sémantique de pile et de l'initialiser avec un objet existant créé avec la sémantique de pile. Un opérateur d'assignation pour un type de référence a une signature au format suivant : `void operator=( R% ){}`.

Si le destructeur de votre type libère des ressources critiques et que vous utilisez la sémantique de pile pour les types référence, vous n’avez pas besoin d’appeler explicitement le destructeur (ou l’appel **`delete`** ). Pour plus d’informations sur les destructeurs dans les types référence, consultez [destructeurs et finaliseurs dans Guide pratique pour définir et consommer des classes et des structs (C++/CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Un opérateur d'assignation généré par le compilateur suit les règles C++ standard habituelles avec les ajouts suivants :

- Toutes les données membres non statiques dont le type est le handle d'un type de référence sont copiées superficiellement (traitées comme des données membres non statiques de type pointeur).

- Toutes les données membres non statiques dont le type est un type de valeur sont copiées superficiellement.

- Toutes les données membres non statiques dont le type est l'instance d'un type de référence font appel au constructeur de copie du type de référence.

Le compilateur fournit également un opérateur unaire `%` pour convertir une instance d'un type de référence créé avec la sémantique de pile en son type de handle sous-jacent.

Les types de référence suivants ne sont pas disponibles pour une utilisation avec la sémantique de pile :

- [delegate (extensions du composant C++)](../extensions/delegate-cpp-component-extensions.md)

- [Tableaux](../extensions/arrays-cpp-component-extensions.md)

- <xref:System.String>

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L'exemple de code suivant indique comment déclarer des instances de types de référence avec la sémantique de pile, comment fonctionne l'opérateur d'affectation et le constructeur de copie, et comment initialiser une référence de suivi avec le type de référence créé grâce à la sémantique de pile.

### <a name="code"></a>Code

```cpp
// stack_semantics_for_reference_types.cpp
// compile with: /clr
ref class R {
public:
   int i;
   R(){}

   // assignment operator
   void operator=(R% r) {
      i = r.i;
   }

   // copy constructor
   R(R% r) : i(r.i) {}
};

void Test(R r) {}   // requires copy constructor

int main() {
   R r1;
   r1.i = 98;

   R r2(r1);   // requires copy constructor
   System::Console::WriteLine(r1.i);
   System::Console::WriteLine(r2.i);

   // use % unary operator to convert instance using stack semantics
   // to its underlying handle
   R ^ r3 = %r1;
   System::Console::WriteLine(r3->i);

   Test(r1);

   R r4;
   R r5;
   r5.i = 13;
   r4 = r5;   // requires a user-defined assignment operator
   System::Console::WriteLine(r4.i);

   // initialize tracking reference
   R % r6 = r4;
   System::Console::WriteLine(r6.i);
}
```

### <a name="output"></a>Output

```Output
98
98
98
13
13
```

## <a name="see-also"></a>Voir aussi

[Classes et structs](../extensions/classes-and-structs-cpp-component-extensions.md)
