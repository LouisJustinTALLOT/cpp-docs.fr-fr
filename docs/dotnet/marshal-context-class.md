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
ms.openlocfilehash: 110fe4abf7eb90b05e7feef563efa4882bed0fc6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332011"
---
# <a name="marshal_context-class"></a>marshal_context, classe

Cette classe convertit les données entre les environnements natifs et gérés.

## <a name="syntax"></a>Syntaxe

```cpp
class marshal_context
```

## <a name="remarks"></a>Notes

Utilisez `marshal_context` la classe pour les conversions de données qui nécessitent un contexte. Pour plus d’informations sur les conversions qui nécessitent un contexte et quel fichier de marshaling doit être inclus, voir [Aperçu de la marshaling dans C .](../dotnet/overview-of-marshaling-in-cpp.md) Le résultat du marshaling lorsque vous utilisez `marshal_context` un contexte n’est valable que jusqu’à ce que l’objet soit détruit. Pour préserver votre résultat, vous devez copier les données.

La `marshal_context` même chose peut être utilisée pour de nombreuses conversions de données. La réutiliser le contexte de cette manière n’affectera pas les résultats des appels de marshaling précédents.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|---------|-----------|
|[marshal_context::marshal_context](#marshal-context)|Construit un `marshal_context` objet à utiliser pour la conversion de données entre les types de données gérés et les types de données autochtones.|
|[marshal_context: :marshal_context](#tilde-marshal-context)|Détruit un objet `marshal_context` .|

### <a name="public-methods"></a>Méthodes publiques

|Nom|Description|
|---------|-----------|
|[marshal_context::marshal_as](#marshal-as)|Effectue le marshaling sur un objet de données spécifique pour le convertir entre un type de données géré et un type de données indigène.|

## <a name="requirements"></a>Spécifications

**Fichier d’en-tête :** \<> msclr-marshal.h, \<> msclr-marshal_windows.h, \<> msclr-marshal_cppstd.h, \<ou> msclr marshal_atl.h

**Namespace:** msclr::interop

## <a name="marshal_contextmarshal_context"></a><a name="marshal-context"></a>marshal_context::marshal_context

Construit un `marshal_context` objet à utiliser pour la conversion de données entre les types de données gérés et les types de données autochtones.

```cpp
marshal_context();
```

### <a name="remarks"></a>Notes

Certaines conversions de données nécessitent un contexte de maréchal. Pour plus d’informations sur les traductions qui nécessitent un contexte et quel fichier de marshaling vous devez inclure dans votre demande, voir [Aperçu de marshaling dans C .](../dotnet/overview-of-marshaling-in-cpp.md)

### <a name="example"></a>Exemple

Voir l’exemple pour [marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md).

## <a name="marshal_contextmarshal_context"></a><a name="tilde-marshal-context"></a>marshal_context: :marshal_context

Détruit un objet `marshal_context` .

```cpp
~marshal_context();
```

### <a name="remarks"></a>Notes

Certaines conversions de données nécessitent un contexte de maréchal. Consultez [l’aperçu de la mise en candidature dans le CMD](../dotnet/overview-of-marshaling-in-cpp.md) pour plus d’informations sur les traductions qui nécessitent un contexte et quel fichier de mise en service doit être inclus dans votre demande.

La suppression `marshal_context` d’un objet invalidera les données converties par ce contexte. Si vous souhaitez préserver vos `marshal_context` données après la destruction d’un objet, vous devez copier manuellement les données à une variable qui persistera.

## <a name="marshal_contextmarshal_as"></a><a name="marshal-as"></a>marshal_context::marshal_as

Effectue le marshaling sur un objet de données spécifique pour le convertir entre un type de données géré et un type de données indigène.

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>Paramètres

*Entrée*<br/>
[dans] La valeur que vous voulez `To_Type` mobiliser à une variable.

### <a name="return-value"></a>Valeur retournée

Une variable `To_Type` de type qui est `input`la valeur convertie de .

### <a name="remarks"></a>Notes

Cette fonction effectue le marshaling sur un objet de données spécifique. Utilisez cette fonction uniquement avec les conversions indiquées par le tableau dans [Aperçu du marshaling dans C .](../dotnet/overview-of-marshaling-in-cpp.md)

Si vous essayez de mobiliser une paire de `marshal_as` types de données qui ne sont pas pris en charge, générera une erreur [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) au moment de la compilation. Lisez le message fourni avec cette erreur pour plus d’informations. L’erreur `C4996` peut être générée pour plus que des fonctions simplement dépréciées. Deux conditions qui génèrent cette erreur sont d’essayer de mobiliser une `marshal_as` paire de types de données qui ne sont pas pris en charge et d’essayer d’utiliser pour une conversion qui nécessite un contexte.

La bibliothèque de marshaling se compose de plusieurs fichiers d’en-tête. Toute conversion ne nécessite qu’un seul fichier, mais vous pouvez inclure des fichiers supplémentaires si vous en avez besoin pour d’autres conversions. Le tableau `Marshaling Overview in C++` indique quel fichier de marshaling doit être inclus pour chaque conversion.

### <a name="example"></a>Exemple

Cet exemple crée un contexte `System::String` pour `const char *` le marshaling d’un type variable. Les données converties ne seront pas valides après la ligne qui supprime le contexte.

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
