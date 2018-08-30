---
title: classe Enum (Extensions du composant C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 625b99751c570c47456aad4903de5b8c4049ac42
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207600"
---
# <a name="enum-class--c-component-extensions"></a>enum, classe (extensions du composant C++)

Déclare une énumération dans la portée espace de noms, qui est un type défini par l’utilisateur composé d’un ensemble de constantes nommées appelées « énumérateurs ».

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="remarks"></a>Notes

C++ / c++ / CX et c++ / prise en charge de l’interface CLI **classe enum publique** et **classe enum privée** qui sont similaires à la norme C++ **classe enum** mais avec l’ajout de l’accessibilité spécificateur. Sous **/CLR**, C ++ 11 **classe enum** type est autorisé, mais génère l’avertissement C4472 qui vise à s’assurer que vous voulez bien le type d’énumération ISO et pas le C + c++ / CX et c++ / type CLI. Pour plus d’informations sur la norme ISO C++ Standard **enum** mot clé, consultez [énumérations](../cpp/enumerations-cpp.md).

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

*access*  
L’accessibilité de l’énumération, qui peut être **public** ou **privé**.

*enumeration-identifier*  
Nom de l’énumération.

*underlying-type*  
(Facultatif) Type sous-jacent de l’énumération.

(Facultatif, Windows Runtime uniquement) le type sous-jacent de l’énumération, qui peut être **bool**, **char**, `char16`, `int16`, `uint16`, **int**, `uint32`, `int64`, ou `uint64`.

*enumerator-list*  
Liste délimitée par des virgules de noms d’énumérateurs.

La valeur de chaque énumérateur est une expression constante définie implicitement par le compilateur ou explicitement par la notation, *enumerator*`=`*constant-expression*. Par défaut, la valeur du premier énumérateur est égale à zéro si elle est définie implicitement. La valeur de chaque énumérateur défini implicitement suivant est égale à la valeur de l’énumérateur précédent + 1.

*var*  
(Facultatif) Nom d’une variable du type de l’énumération.

### <a name="remarks"></a>Notes

Pour plus d’informations et d’exemples, consultez [Enums](https://msdn.microsoft.com/%20library/windows/apps/hh755820.aspx).

Notez que le compilateur émet des messages d’erreur si l’expression constante qui définit la valeur d’un énumérateur ne peut pas être représentée par *underlying-type*.  Cependant, le compilateur ne signale pas d’erreur pour une valeur non appropriée pour le type sous-jacent. Exemple :

- Si *underlying-type* a la valeur numeric et qu’un énumérateur spécifie la valeur maximale pour ce type, la valeur de la prochaine énumération définie implicitement ne peut pas être représentée.

- Si *type sous-jacent* est **bool**, et plus de deux énumérateurs sont implicitement définis, les énumérateurs qui suivent les deux premières ne peut pas être représentés.

- Si *underlying-type* a la valeur `char16`et que la valeur d’énumération est comprise entre 0xD800 et 0xDFFF, la valeur peut être représentée. Cependant, la valeur est logiquement incorrecte, car elle représente la moitié d’une paire de substitution Unicode et ne doit pas apparaître de façon isolée.

### <a name="requirements"></a>Configuration requise

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

*access*  
Accessibilité de l’énumération. Peut être **public** ou **privé**.

*enumerator-list*  
Liste délimitée par des virgules des identificateurs (énumérateurs) contenus dans l'énumération.

*name*  
Nom de l’énumération. Les énumérations managées anonymes ne sont pas autorisées.

*type* (facultatif)  
Type sous-jacent des *identificateurs*. Cela peut être tout type scalaire, telles que les versions signés ou de **int**, **court**, ou **long**.  **bool** ou **char** est également autorisé.

*var* (facultatif)  
Nom d’une variable du type de l’énumération.

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

Dans Visual C++ 2002 et Visual C++ 2003, les énumérateurs étaient faiblement injectés (visibles dans la portée englobante, sauf en présence d’un autre identificateur de même nom).

Si une énumération C++ standard est définie (sans **classe** ou **struct**) et que vous compilez avec `/clr` entraîne l’énumération sera compilée en tant qu’une énumération gérée.  L’énumération conserve la sémantique d’une énumération non managée.  Notez que le compilateur injecte un attribut, `Microsoft::VisualC::NativeEnumAttribute`, qui est reconnu par le compilateur Visual C++, pour montrer que le programmeur souhaite faire de l’énumération une énumération native.  Les autres compilateurs considèrent simplement l’énumération standard comme une énumération gérée.

A nommé, énumération standard compilée avec `/clr` seront visibles dans l’assembly en tant qu’une énumération gérée et peuvent être utilisées par n’importe quel autre compilateur managé.   En revanche, une énumération standard sans nom n’est pas visible publiquement à partir de l’assembly.

Dans Visual C++ 2002 et Visual C++ 2003, une énumération standard utilisée comme type dans un paramètre de fonction :

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

### <a name="requirements"></a>Configuration requise

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

[Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)