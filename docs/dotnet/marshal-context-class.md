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
ms.openlocfilehash: 25fc2be80ba0e5d8c7f76cee1f22eed4d1bb4fc7
ms.sourcegitcommit: 9813e146a4eb30929d8352872859e8fcb7ff6d2f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805979"
---
# <a name="marshalcontext-class"></a>marshal_context, classe

Cette classe convertit des données entre les environnements natifs et managés.

## <a name="syntax"></a>Syntaxe

```cpp
class marshal_context
```

## <a name="remarks"></a>Notes

Utilisez la `marshal_context` classe pour les conversions de données qui requièrent un contexte. Pour plus d’informations sur les conversions nécessitent un contexte et quel fichier marshaling doit être inclus, consultez [vue d’ensemble du marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md). Le résultat du marshaling lorsque vous utilisez un contexte est valide uniquement jusqu'à la `marshal_context` objet est détruit. Pour conserver votre résultat, vous devez copier les données.

Le même `marshal_context` peut être utilisé pour les conversions de nombreuses données. Réutiliser le contexte de cette manière n’affecte pas les résultats des appels de marshaling précédents.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description| 
|---------|-----------| 
|[marshal_context::marshal_context](#marshal-context)|Construit un `marshal_context` objet à utiliser pour la conversion des données entre les types de données managés et natifs.| 
|[marshal_context::~marshal_context](#tilde-marshal-context)|Détruit un objet `marshal_context`.| 

### <a name="public-methods"></a>Méthodes publiques

|Name|Description| 
|---------|-----------| 
|[marshal_context::marshal_as](#marshal-as)|Effectue le marshaling sur un objet de données spécifique pour le convertir entre managé et un type de données natif.| 


## <a name="requirements"></a>Spécifications

**Fichier d’en-tête :** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, ou \<msclr\marshal_atl.h >

**Namespace :** msclr::interop

## <a name="marshal-context"></a>marshal_context::marshal_context

Construit un `marshal_context` objet à utiliser pour la conversion des données entre les types de données managés et natifs.

```cpp
marshal_context();
```

### <a name="remarks"></a>Notes

Certaines conversions de données nécessitent un contexte de marshaler. Pour plus d’informations sur les traductions nécessitent un contexte et le marshaling de fichier que vous devez inclure dans votre application, consultez [vue d’ensemble du marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md).

### <a name="example"></a>Exemple

Consultez l’exemple de [marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md).


## <a name="tilde-marshal-context"></a>marshal_context::~marshal_context

Détruit un objet `marshal_context`.

```cpp
~marshal_context();
```

### <a name="remarks"></a>Notes

Certaines conversions de données nécessitent un contexte de marshaler. Consultez [vue d’ensemble du marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md) pour plus d’informations sur les traductions nécessitent un contexte et quel fichier marshaling doit être inclus dans votre application.

Suppression d’un `marshal_context` objet invalidera les données converties par ce contexte. Si vous souhaitez conserver vos données après un `marshal_context` objet est détruit, vous devez copier manuellement les données à une variable qui est conservé.

## <a name="marshal-as"></a>marshal_context::marshal_as

Effectue le marshaling sur un objet de données spécifique pour le convertir entre managé et un type de données natif.

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>Paramètres

*input*<br/>
[in] La valeur que vous souhaitez à marshaler en un `To_Type` variable.

### <a name="return-value"></a>Valeur de retour

Une variable de type `To_Type` qui est la valeur convertie de `input`.

### <a name="remarks"></a>Notes

Cette fonction effectue le marshaling sur un objet de données spécifique. Utilisez cette fonction uniquement avec les conversions indiquées par la table dans [vue d’ensemble du marshaling dans C++](../dotnet/overview-of-marshaling-in-cpp.md).

Si vous tentez de marshaler une paire de types de données qui ne sont pas pris en charge, `marshal_as` générera une erreur [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) au moment de la compilation. Lire le message fourni avec cette erreur pour plus d’informations. Le `C4996` erreur peut être générée pour les fonctions plus de simplement déconseillées. Deux conditions qui génèrent cette erreur sont essaie de marshaler une paire de types de données qui ne sont pas pris en charge et essaie d’utiliser `marshal_as` pour une conversion qui requiert un contexte.

La bibliothèque de marshaling se compose de plusieurs fichiers d’en-tête. Toute conversion ne nécessite qu’un seul fichier, mais vous pouvez inclure des fichiers supplémentaires si vous avez besoin pour les autres conversions. Le tableau dans `Marshaling Overview in C++` indique quel fichier marshaling doit être inclus pour chaque conversion.

### <a name="example"></a>Exemple

Cet exemple crée un contexte pour le marshaling d’un `System::String` à un `const char *` type de variable. Les données converties sera valides après la ligne qui supprime le contexte.

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