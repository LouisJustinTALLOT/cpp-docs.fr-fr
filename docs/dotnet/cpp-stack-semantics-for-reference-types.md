---
title: Sémantique de pile C++ pour les Types référence | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- reference types, C++ stack semantics for
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: df14886daa04d4905502341ef345c3e3afa595ff
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410622"
---
# <a name="c-stack-semantics-for-reference-types"></a>Sémantique de pile C++ pour les types de référence

Avant Visual C++ 2005, une instance d'un type de référence pouvait être créée à l'aide de l'opérateur `new`, qui a créé l'objet sur le tas du garbage collector. Toutefois, vous pouvez à présent créer une instance d'un type de référence en utilisant la même syntaxe que vous devriez utiliser pour créer une instance d'un type natif dans la pile. Par conséquent, vous n’avez pas besoin d’utiliser [gcnew nouvelle, ref](../windows/ref-new-gcnew-cpp-component-extensions.md) pour créer un objet d’un type référence. Et lorsque l'objet est hors de portée, le compilateur appelle le destructeur de l'objet.

## <a name="remarks"></a>Notes

Lorsque vous créez une instance d'un type de référence à l'aide de la sémantique de pile, le compilateur crée en interne l'instance sur le segment récupéré par le garbage collector (utilisation de `gcnew`).

Lorsque la signature ou le type de retour d’une fonction inclut une instance d’un type de référence par valeur, la fonction est marquée dans les métadonnées comme nécessitant une gestion spéciale (avec modreq). Cette gestion spéciale est actuellement fournie par les clients Visual C++ ; les autres langues ne prennent pas en charge les fonctions "gourmandes" ou les données qui utilisent les types de référence créés avec la sémantique de pile.

Il est souhaitable d'utiliser `gcnew` (allocation dynamique) au lieu de la sémantique de pile si le type n'a aucun destructeur. En outre, l'utilisation de types de référence créés avec la sémantique de pile dans les signatures de fonction ne serait pas possible si vous souhaitez que vos fonctions soient utilisées dans des langages autres que Visual C++.

Le compilateur ne génère pas de constructeur de copies pour un type de référence. Par conséquent, si vous définissez une fonction qui utilise un type de référence pour chaque valeur dans la signature, vous devez définir un constructeur de copie pour le type de référence. Un constructeur de copie pour un type de référence possède une signature au format suivant : `R(R%){}`.

Le compilateur ne génère pas d'opérateur d'affectation par défaut pour un type de référence. Un opérateur d'affectation vous permet de créer un objet avec la sémantique de pile et de l'initialiser avec un objet existant créé avec la sémantique de pile. Un opérateur d'assignation pour un type de référence a une signature au format suivant : `void operator=( R% ){}`.

Si le destructeur de votre type libère les ressources critiques et que vous utilisez la sémantique de pile pour les types de référence, vous n'avez pas besoin d'appeler explicitement le destructeur (ou appeler `delete`). Pour plus d’informations sur les destructeurs dans les types référence, consultez [destructeurs et finaliseurs dans Comment : définir et consommer des classes et structs (C++ / c++ / CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Un opérateur d'assignation généré par le compilateur suit les règles C++ standard habituelles avec les ajouts suivants :

- Toutes les données membres non statiques dont le type est le handle d'un type de référence sont copiées superficiellement (traitées comme des données membres non statiques de type pointeur).

- Toutes les données membres non statiques dont le type est un type de valeur sont copiées superficiellement.

- Toutes les données membres non statiques dont le type est l'instance d'un type de référence font appel au constructeur de copie du type de référence.

Le compilateur fournit également un opérateur unaire `%` pour convertir une instance d'un type de référence créé avec la sémantique de pile en son type de handle sous-jacent.

Les types de référence suivants ne sont pas disponibles pour une utilisation avec la sémantique de pile :

- [delegate (extensions du composant C++)](../windows/delegate-cpp-component-extensions.md)

- [Tableaux](../windows/arrays-cpp-component-extensions.md)

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

### <a name="output"></a>Sortie

```Output
98
98
98
13
13
```

## <a name="see-also"></a>Voir aussi

[Classes et structs](../windows/classes-and-structs-cpp-component-extensions.md)