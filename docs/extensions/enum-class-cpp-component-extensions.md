---
title: classe enum (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
ms.openlocfilehash: 9acf93976b2f7751e85bf3ed0ddd2735c29e121c
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590314"
---
# <a name="enum-class--ccli-and-ccx"></a>classe enum (C++/CLI et C++/CX)

Déclare une énumération dans la portée espace de noms, qui est un type défini par l’utilisateur composé d’un ensemble de constantes nommées appelées « énumérateurs ».

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="remarks"></a>Notes

Les langages C++/CX et C++/CLI prennent en charge **public enum class** et **private enum class**, qui sont similaires à la classe C++ standard **enum class**, mais avec l’ajout du spécificateur d’accessibilité. Sous **/clr**, le type C++11 **enum class** est autorisé, mais il génère l’avertissement C4472 qui vise à s’assurer que vous voulez bien le type d’énumération ISO et non le type C++/CX et C++/CLI. Pour plus d’informations sur le mot clé ISO C++ standard **`enum`** , consultez [énumérations](../cpp/enumerations-cpp.md).

## <a name="windows-runtime"></a>Windows Runtime

### <a name="syntax"></a>Syntaxe

```cpp
      access
      enum class
      enumeration-identifier
      [:underlying-type] { enumerator-list } [var];
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];
```

### <a name="parameters"></a>Paramètres

*accéder*<br/>
Accessibilité de l’énumération, qui peut être **`public`** ou **`private`** .

*enumeration-identifier*<br/>
Nom de l’énumération.

*type sous-jacent*<br/>
(Facultatif) Type sous-jacent de l’énumération.

(Facultatif, Windows Runtime uniquement) le type sous-jacent de l’énumération, qui peut être **`bool`** , **`char`** , `char16` , `int16` , `uint16` , **`int`** , `uint32` , `int64` ou `uint64` .

*enumerator-list*<br/>
Liste délimitée par des virgules de noms d’énumérateurs.

La valeur de chaque énumérateur est une expression constante qui est définie implicitement par le compilateur, ou explicitement par la notation, *enumerator* `=` *expression constante*d’énumérateur. Par défaut, la valeur du premier énumérateur est égale à zéro si elle est définie implicitement. La valeur de chaque énumérateur défini implicitement suivant est égale à la valeur de l’énumérateur précédent + 1.

*var*<br/>
(Facultatif) Nom d’une variable du type de l’énumération.

### <a name="remarks"></a>Notes

Pour plus d’informations et d’exemples, consultez [Énumérations](../cppcx/enums-c-cx.md).

Notez que le compilateur émet des messages d’erreur si l’expression constante qui définit la valeur d’un énumérateur ne peut pas être représentée par *underlying-type*.  Cependant, le compilateur ne signale pas d’erreur pour une valeur non appropriée pour le type sous-jacent. Par exemple :

- Si le *type sous-jacent* est numérique et qu’un énumérateur spécifie la valeur maximale pour ce type, la valeur de l’énumération implicitement définie suivante ne peut pas être représentée.

- Si le *type sous-jacent* est **`bool`** , et que plus de deux énumérateurs sont implicitement définis, les énumérateurs qui suivent les deux premiers ne peuvent pas être représentés.

- Si *underlying-type* a la valeur `char16`et que la valeur d’énumération est comprise entre 0xD800 et 0xDFFF, la valeur peut être représentée. Cependant, la valeur est logiquement incorrecte, car elle représente la moitié d’une paire de substitution Unicode et ne doit pas apparaître de façon isolée.

### <a name="requirements"></a>Exigences

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Syntaxe

```cpp
      access
      enum class
      name [:type] { enumerator-list } var;
accessenum structname [:type] { enumerator-list } var;
```

### <a name="parameters"></a>Paramètres

*accéder*<br/>
Accessibilité de l’énumération. Peut avoir la valeur **`public`** ou **`private`** .

*enumerator-list*<br/>
Liste délimitée par des virgules des identificateurs (énumérateurs) contenus dans l'énumération.

*name*<br/>
Nom de l’énumération. Les énumérations managées anonymes ne sont pas autorisées.

*type*<br/>
(Facultatif) Type sous-jacent des *identificateurs*. Il peut s’agir de n’importe quel type scalaire, tel que des versions signées ou non signées de **`int`** , **`short`** ou **`long`** .  **`bool`** ou **`char`** est également autorisé.

*var*<br/>
(Facultatif) Nom d’une variable du type de l’énumération.

### <a name="remarks"></a>Notes

**enum class** et **enum struct** sont des déclarations équivalentes.

Il existe deux types d’énumération : managé ou C++/CX et standard.

Une énumération managée ou C++/CX peut être définie comme suit :

```cpp
public enum class day {sun, mon };
```

et est l’équivalent sémantique de :

```cpp
ref class day {
public:
   static const int sun = 0;
   static const int mon = 1;
};
```

Une énumération standard peut être définie comme suit :

```cpp
enum day2 { sun, mon };
```

et est l’équivalent sémantique de :

```cpp
static const int sun = 0;
static const int mon = 1;
```

Les noms d’énumérateurs managés (*identificateurs*) ne sont pas injectés dans la portée où est définie l’énumération ; toutes les références aux énumérateurs doivent être des noms qualifiés complets (*nom*`::`*identificateur*).  Pour cette raison, vous ne pouvez pas définir une énumération managée anonyme.

Les énumérateurs d’une énumération standard sont fortement injectés dans la portée englobante.  Autrement dit, si un autre symbole a le même nom qu’un énumérateur dans la portée englobante, le compilateur génère une erreur.

Dans Visual Studio 2002 et Visual Studio 2003, les énumérateurs étaient faiblement injectés (visibles dans la portée englobante, sauf en présence d’un autre identificateur de même nom).

Si une énumération C++ standard est définie (sans **`class`** ou **`struct`** ), la compilation avec entraîne la compilation de `/clr` l’énumération en tant qu’énumération managée.  L’énumération conserve la sémantique d’une énumération non managée.  Notez que le compilateur injecte un attribut, `Microsoft::VisualC::NativeEnumAttribute`, pour montrer que le programmeur souhaite faire de l’énumération une énumération native.  Les autres compilateurs considèrent simplement l’énumération standard comme une énumération gérée.

Une énumération nommée standard compilée avec `/clr` est visible dans l’assembly en tant qu’énumération managée et peut être utilisée par n’importe quel autre compilateur managé.   En revanche, une énumération standard sans nom n’est pas visible publiquement à partir de l’assembly.

Dans Visual Studio 2002 et Visual Studio 2003, une énumération standard utilisée comme type dans un paramètre de fonction :

```cpp
// mcppv2_enum.cpp
// compile with: /clr
enum E { a, b };
void f(E) {System::Console::WriteLine("hi");}

int main() {
   E myi = b;
   f(myi);
}
```

émettrait la ligne ci-dessous dans le langage MSIL pour la signature de fonction :

```cpp
void f(int32);
```

Cependant, dans les versions actuelles du compilateur, l’énumération standard est émise en tant qu’énumération managée avec un [NativeEnumAttribute] et la ligne ci-dessous dans le langage MSIL pour la signature de fonction :

```cpp
void f(E)
```

Pour plus d'informations sur les énumérations natives, consultez [Déclarations d'énumération C++](../cpp/enumerations-cpp.md).

Pour plus d’informations sur les énumérations CLR, consultez :

- [Type sous-jacent d’une énumération](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)

### <a name="requirements"></a>Exigences

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

```cpp
// mcppv2_enum_2.cpp
// compile with: /clr
// managed enum
public enum class m { a, b };

// standard enum
public enum n { c, d };

// unnamed, standard enum
public enum { e, f } o;

int main()
{
   // consume managed enum
   m mym = m::b;
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);
   System::Console::WriteLine("convert to int: {0}", (int)mym);

   // consume standard enum
   n myn = d;
   System::Console::WriteLine(myn);

   // consume standard, unnamed enum
   o = f;
   System::Console::WriteLine(o);
}
```

```Output
no automatic conversion to int: b

convert to int: 1

1

1
```

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour .NET et UWP](component-extensions-for-runtime-platforms.md)
