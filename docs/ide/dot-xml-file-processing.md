---
title: Traitement de fichier.Xml
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation, processing XML file
ms.assetid: e70fdeae-80ac-4872-ab24-771c5635cfbf
ms.openlocfilehash: bc9aa57ffd68630d0a4209f8f8611882f8f36fc3
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524168"
---
# <a name="xml-file-processing"></a>Traitement de fichier.Xml

Le compilateur génère une chaîne d’ID pour chaque construction de votre code qui est marquée pour générer la documentation. Pour plus d’informations, consultez [Balises recommandées pour les commentaires de documentation](../ide/recommended-tags-for-documentation-comments-visual-cpp.md). La chaîne d’ID identifie de façon unique la construction. Les programmes qui traitent le fichier .xml peuvent utiliser la chaîne d’ID pour identifier l’élément de métadonnées/réflexion .NET Framework correspondant auquel s’applique la documentation.

Le fichier .xml n’est pas une représentation hiérarchique de votre code, il s’agit d’une liste plate avec un ID généré pour chaque élément.

Le compilateur respecte les règles suivantes quand il génère les chaînes d’ID :

- La chaîne ne contient aucun espace blanc.

- La première partie de la chaîne d’ID identifie le type du membre, avec un caractère unique suivi de deux-points. Les types de membres suivants sont utilisés :

  | Caractère | Description |
  |---------------|-----------------|
  | N | namespace<br /><br /> Vous ne pouvez pas ajouter de commentaires de documentation à un espace de noms, mais des références cref à un espace de noms sont possibles. |
  | T | type : classe, interface, struct, enum, délégué |
  | D | typedef |
  | F | champ |
  | P | propriété (notamment des indexeurs ou autres propriétés indexées) |
  | M | méthode (notamment des méthodes spéciales telles que des constructeurs, des opérateurs, etc.) |
  | E | événement |
  | ! | chaîne d’erreur<br /><br /> Le reste de la chaîne fournit des informations sur l’erreur. Le compilateur Visual C++ génère des informations d’erreur pour les liens qui ne peuvent pas être résolus. |

- La deuxième partie de la chaîne est le nom qualifié complet de l’élément, en commençant à la racine de l’espace de noms. Le nom de l’élément, son ou ses types englobants et l’espace de noms sont séparés par des points. Si le nom de l’élément lui-même comporte des points, ceux-ci sont remplacés par un signe dièse (« # »). On suppose qu’aucun élément n’a de signe dièse directement dans son nom. Par exemple, le nom complet du constructeur `String` est « System.String.#ctor ».

- Pour les propriétés et méthodes, si la méthode a des arguments, la liste d’arguments entre parenthèses suit. S’il n’y a pas d’arguments, aucune parenthèse n’est présente. Les arguments sont séparés par des virgules. L’encodage de chaque argument correspond directement à son encodage dans une signature .NET Framework :

  - Types de base. Les types réguliers (ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE) sont représentés en tant que nom qualifié complet du type.

  - Les types intrinsèques (par exemple ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF et ELEMENT_TYPE_VOID) sont représentés comme le nom complet du type complet correspondant, par exemple, **System.Int32** ou **System.TypedReference**.

  - ELEMENT_TYPE_PTR est représenté par un « * » après le type modifié.

  - ELEMENT_TYPE_BYREF est représenté par un '\@' après le type modifié.

  - ELEMENT_TYPE_PINNED est représenté par un « ^ » après le type modifié. Le compilateur Visual C++ ne génère jamais ceci.

  - ELEMENT_TYPE_CMOD_REQ est représenté par un « &#124; » et le nom qualifié complet de la classe de modification, après le type modifié. Le compilateur Visual C++ ne génère jamais ceci.

  - ELEMENT_TYPE_CMOD_OPT est représenté par un « ! » et le nom qualifié complet de la classe de modification, après le type modifié.

  - ELEMENT_TYPE_SZARRAY est représenté par « [] » après le type d’élément du tableau.

  - ELEMENT_TYPE_GENERICARRAY est représenté par « [?] » après le type d’élément du tableau. Le compilateur Visual C++ ne génère jamais ceci.

  - ELEMENT_TYPE_ARRAY est représenté par [*limite_inférieure*:`size`,*limite_supérieure*:`size`], où le nombre de virgules correspond au rang - 1, et la limite inférieure et la taille de chaque dimension, si elles sont connues, sont représentées sous forme décimale. Si la limite inférieure ou la taille n’est pas spécifiée, elle est simplement omise. Si la limite inférieure et la taille d’une dimension particulière sont omises, le « : » est également omis. Par exemple, un tableau à deux dimensions avec 1 comme limite inférieure et une taille non spécifiée est [1:,1:].

  - ELEMENT_TYPE_FNPTR est représenté en tant que « =FUNC:`type`(*signature*) », où `type` est le type de retour et *signature* correspond aux arguments de la méthode. S’il n’y a pas d’argument, les parenthèses sont omises. Le compilateur Visual C++ ne génère jamais ceci.

  Les composants de signature suivants ne sont pas représentés, car ils ne sont jamais utilisés pour différencier les méthodes surchargées :

  - convention d’appel

  - type de retour

  - ELEMENT_TYPE_SENTINEL

- Pour les opérateurs de conversion uniquement, la valeur de retour de la méthode est encodée sous la forme « ~ », suivi du type de retour, conformément à l’encodage ci-dessus.

- Pour les types génériques, le nom du type est suivi d’un accent grave, puis d’un chiffre qui indique le nombre de paramètres de type générique.  Par exemple :

    ```xml
    <member name="T:MyClass`2">
    ```

  pour un type défini comme `public class MyClass<T, U>`.

  Pour les méthodes qui prennent des types génériques comme paramètres, les paramètres de type générique sont spécifiés sous forme de chiffres précédés d’accents graves (par exemple \`0, \`1).  Chaque chiffre représente une notation de tableau de base zéro pour les paramètres génériques du type.

## <a name="example"></a>Exemple

Les exemples suivants montrent comment les chaînes d’ID pour une classe et ses membres sont générées.

```cpp
// xml_id_strings.cpp
// compile with: /clr /doc /LD
///
namespace N {
// "N:N"

   /// <see cref="System" />
   //  <see cref="N:System"/>
   ref class X {
   // "T:N.X"

   protected:
      ///
      !X(){}
      // "M:N.X.Finalize", destructor's representation in metadata

   public:
      ///
      X() {}
      // "M:N.X.#ctor"

      ///
      static X() {}
      // "M:N.X.#cctor"

      ///
      X(int i) {}
      // "M:N.X.#ctor(System.Int32)"

      ///
      ~X() {}
      // "M:N.X.Dispose", Dispose function representation in metadata

      ///
      System::String^ q;
      // "F:N.X.q"

      ///
      double PI;
      // "F:N.X.PI"

      ///
      int f() { return 1; }
      // "M:N.X.f"

      ///
      int bb(System::String ^ s, int % y, void * z) { return 1; }
      // "M:N.X.bb(System.String,System.Int32@,System.Void*)"

      ///
      int gg(array<short> ^ array1, array< int, 2 >^ IntArray) { return 0; }
      // "M:N.X.gg(System.Int16[], System.Int32[0:,0:])"

      ///
      static X^ operator+(X^ x, X^ xx) { return x; }
     // "M:N.X.op_Addition(N.X,N.X)"

      ///
      property int prop;
      // "M:N.X.prop"

      ///
      property int prop2 {
      // "P:N.X.prop2"

         ///
         int get() { return 0; }
         // M:N.X.get_prop2

         ///
         void set(int i) {}
         // M:N.X.set_prop2(System.Int32)
      }

      ///
      delegate void D(int i);
      // "T:N.X.D"

      ///
      event D ^ d;
      // "E:N.X.d"

      ///
      ref class Nested {};
      // "T:N.X.Nested"

      ///
      static explicit operator System::Int32 (X x) { return 1; }
      // "M:N.X.op_Explicit(N.X!System.Runtime.CompilerServices.IsByValue)~System.Int32"
   };
}
```

## <a name="see-also"></a>Voir aussi

[Documentation XML](../ide/xml-documentation-visual-cpp.md)