---
title: marshal_context, classe
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- msclr::interop::marshal_context::marshal_as
helpviewer_keywords:
- msclr::marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
ms.openlocfilehash: aa5935332cfa12c02e8084136a311a7593a4f3b9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508581"
---
# <a name="marshal_context-class"></a>marshal_context, classe

Cette classe convertit les données entre les environnements natifs et managés.

## <a name="syntax"></a>Syntaxe

```cpp
class marshal_context
```

## <a name="remarks"></a>Notes

Utilisez la `marshal_context` classe pour les conversions de données qui requièrent un contexte. Pour plus d’informations sur les conversions qui requièrent un contexte et le fichier de marshaling à inclure, consultez [vue d’ensemble du marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md). Le résultat du marshaling lorsque vous utilisez un contexte est valide uniquement jusqu’à ce que l' `marshal_context` objet soit détruit. Pour conserver votre résultat, vous devez copier les données.

Le même `marshal_context` peut être utilisé pour de nombreuses conversions de données. La réutilisation du contexte de cette manière n’affecte pas les résultats des appels de marshaling précédents.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|---------|-----------|
|[marshal_context::marshal_context](#marshal-context)|Construit un `marshal_context` objet à utiliser pour la conversion de données entre des types de données managées et natifs.|
|[marshal_context :: ~ marshal_context](#tilde-marshal-context)|Détruit un objet `marshal_context` .|

### <a name="public-methods"></a>Méthodes publiques

|Nom|Description|
|---------|-----------|
|[marshal_context::marshal_as](#marshal-as)|Effectue le marshaling sur un objet de données spécifique pour le convertir entre un type de données managé et un type de données natif.|

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête :** \<msclr\marshal.h> , \<msclr\marshal_windows.h> , \<msclr\marshal_cppstd.h> ou \<msclr\marshal_atl.h>

**Espace de noms :** msclr, :: Interop

## <a name="marshal_contextmarshal_context"></a><a name="marshal-context"></a> marshal_context :: marshal_context

Construit un `marshal_context` objet à utiliser pour la conversion de données entre des types de données managées et natifs.

```cpp
marshal_context();
```

### <a name="remarks"></a>Remarques

Certaines conversions de données requièrent un contexte Marshal. Pour plus d’informations sur les traductions qui requièrent un contexte et le fichier de marshaling que vous devez inclure dans votre application, consultez [vue d’ensemble du marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md).

### <a name="example"></a>Exemple

Consultez l’exemple de [marshal_context :: marshal_as](#marshal-as).

## <a name="marshal_contextmarshal_context"></a><a name="tilde-marshal-context"></a> marshal_context :: ~ marshal_context

Détruit un objet `marshal_context` .

```cpp
~marshal_context();
```

### <a name="remarks"></a>Remarques

Certaines conversions de données requièrent un contexte Marshal. Consultez [vue d’ensemble du marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md) pour plus d’informations sur les traductions qui requièrent un contexte et le fichier de marshaling à inclure dans votre application.

La suppression d’un `marshal_context` objet invalidera les données converties par ce contexte. Si vous souhaitez conserver vos données après la destruction d’un `marshal_context` objet, vous devez copier manuellement les données dans une variable qui sera conservée.

## <a name="marshal_contextmarshal_as"></a><a name="marshal-as"></a> marshal_context :: marshal_as

Effectue le marshaling sur un objet de données spécifique pour le convertir entre un type de données managé et un type de données natif.

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>Paramètres

*input*<br/>
dans Valeur que vous souhaitez marshaler en une `To_Type` variable.

### <a name="return-value"></a>Valeur renvoyée

Variable de type `To_Type` qui est la valeur convertie de `input` .

### <a name="remarks"></a>Remarques

Cette fonction effectue le marshaling sur un objet de données spécifique. Utilisez cette fonction uniquement avec les conversions indiquées par le tableau dans [vue d’ensemble du marshaling en C++](../dotnet/overview-of-marshaling-in-cpp.md).

Si vous essayez de marshaler une paire de types de données qui ne sont pas pris en charge, `marshal_as` génère une erreur [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) au moment de la compilation. Pour plus d’informations, lisez le message fourni avec cette erreur. L' `C4996` erreur peut être générée pour des fonctions plus que simplement dépréciées. Deux conditions qui génèrent cette erreur essaient de marshaler une paire de types de données qui ne sont pas pris en charge et qui essaient d’utiliser `marshal_as` pour une conversion qui requiert un contexte.

La bibliothèque de marshaling se compose de plusieurs fichiers d’en-tête. Toute conversion requiert un seul fichier, mais vous pouvez inclure des fichiers supplémentaires si nécessaire pour d’autres conversions. La table dans `Marshaling Overview in C++` indique quel fichier de marshaling doit être inclus pour chaque conversion.

### <a name="example"></a>Exemple

Cet exemple crée un contexte pour le marshaling d’un `System::String` vers un `const char *` type de variable. Les données converties ne sont pas valides après la ligne qui supprime le contexte.

```cpp
// marshal_context_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   marshal_context^ context = gcnew marshal_context();
   String^ message = gcnew String("Test String to Marshal");
   const char* result;
   result = context->marshal_as<const char*>( message );
   delete context;
   return 0;
}
```
