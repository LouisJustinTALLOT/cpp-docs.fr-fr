---
title: Macros d’options du compilateur
ms.date: 08/19/2019
f1_keywords:
- _ATL_ALL_WARNINGS
- _ATL_APARTMENT_THREADED
- '_ATL_CSTRING_EXPLICIT_CONSTRUCTORS '
- _ATL_ENABLE_PTM_WARNING
- _ATL_FREE_THREADED
- _ATL_MULTI_THREADED
- _ATL_NO_AUTOMATIC_NAMESPACE
- _ATL_NO_COM_SUPPORT
- ATL_NO_VTABLE
- ATL_NOINLINE
- _ATL_SINGLE_THREADED
helpviewer_keywords:
- compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
ms.openlocfilehash: 84083c696ee7bdcbb9538bf587c4aaded7a3932e
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630643"
---
# <a name="compiler-options-macros"></a>Macros d’options du compilateur

Ces macros contrôlent des fonctionnalités de compilateur spécifiques.

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Symbole qui active des erreurs dans les projets convertis à partir de versions précédentes d’ATL.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Définissez si un ou plusieurs de vos objets utilisent le thread cloisonné.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Rend certains `CString` constructeurs explicites, ce qui évite les conversions non intentionnelles.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Définissez cette macro afin d’utiliser C++ une syntaxe conforme standard, qui génère l’erreur du compilateur C4867 quand une syntaxe non standard est utilisée pour initialiser un pointeur vers une fonction membre.|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Définissez si un ou plusieurs de vos objets utilisent le Threading libre ou neutre.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Symbole qui indique que le projet aura des objets marqués comme étant à la fois, libres ou neutres. La macro [_ATL_FREE_THREADED](#_atl_free_threaded) doit être utilisée à la place.|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Symbole qui empêche l’utilisation par défaut de l’espace de noms comme ATL.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Symbole qui empêche le code lié à COM d’être compilé avec votre projet.|
|[ATL_NO_VTABLE](#atl_no_vtable)|Symbole qui empêche l’initialisation du pointeur vtable dans le constructeur et le destructeur de la classe.|
|[ATL_NOINLINE](#atl_noinline)|Un symbole qui indique qu’une fonction ne doit pas être Inline.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Définissez si tous vos objets utilisent le modèle de thread unique.|

##  <a name="_atl_all_warnings"></a>  _ATL_ALL_WARNINGS

Symbole qui active des erreurs dans les projets convertis à partir de versions précédentes d’ATL.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Notes

Avant Visual C++ .NET 2002, les ATL ont désactivé de nombreux avertissements et les ont laissés désactivés afin qu’ils ne soient jamais affichés dans le code utilisateur. Plus précisément :

- L’expression conditionnelle C4127 est constante

- C4786 'identificateur': l’identificateur a été tronqué en caractères’nombre’dans les informations de débogage

- Extension C4201 non standard utilisée: struct/union sans type

- C4103 'nom_fichier': utilisé #pragma Pack pour modifier l’alignement

- C4291 'declaration': aucune suppression d’opérateur correspondante trouvée; la mémoire ne sera pas libérée si l’initialisation lève une exception

- C4268 'identifier': les données statiques/globales’const’initialisées avec le constructeur par défaut généré par le compilateur remplissent l’objet de zéros

- Code inaccessible C4702

Dans les projets convertis à partir de versions précédentes, ces avertissements sont toujours désactivés par les en-têtes de bibliothèques.

Si vous ajoutez la ligne suivante au fichier *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures) avant d’inclure les en-têtes de bibliothèques, ce comportement peut être modifié.

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

Si cette `#define` valeur est ajoutée, les en-têtes ATL sont vigilants pour conserver l’état de ces avertissements afin qu’ils ne soient pas désactivés globalement (ou si l’utilisateur désactive explicitement les avertissements individuels, et non pour les activer).

Les nouveaux projets sont `#define` définis dans *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures) par défaut.

##  <a name="_atl_apartment_threaded"></a>  _ATL_APARTMENT_THREADED

Définissez si un ou plusieurs de vos objets utilisent le thread cloisonné.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Notes

Spécifie le thread cloisonné. Consultez [spécification du modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour d’autres options de Threading, et [options, Assistant objet simple ATL](../../atl/reference/options-atl-simple-object-wizard.md) pour obtenir une description des modèles de thread disponibles pour un objet ATL.

##  <a name="_atl_cstring_explicit_constructors"></a>  _ATL_CSTRING_EXPLICIT_CONSTRUCTORS

Rend certains `CString` constructeurs explicites, ce qui évite les conversions non intentionnelles.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Notes

Quand ce constructeur est défini, tous les constructeurs CString qui acceptent un paramètre unique sont compilés avec le mot clé Explicit, qui empêche les conversions implicites des arguments d’entrée. Cela signifie, par exemple, que lorsque _ Unicode est défini, si vous tentez d’utiliser une chaîne CHAR * comme argument de constructeur CString, une erreur de compilateur se produit. Utilisez cette macro dans les situations où vous devez éviter les conversions implicites entre les types de chaînes étroits et larges.

En utilisant la macro _ t sur tous les arguments de chaîne de constructeur, vous pouvez définir _ATL_CSTRING_EXPLICIT_CONSTRUCTORS et éviter les erreurs de compilation, que _ Unicode soit défini ou non.

##  <a name="_atl_enable_ptm_warning"></a>  _ATL_ENABLE_PTM_WARNING

Définissez cette macro afin de forcer l’utilisation de la syntaxe C++ conforme à la norme ANSI pour les fonctions de pointeur vers membre. L’utilisation de cette macro entraîne la génération de l’erreur du compilateur C4867 quand une syntaxe non standard est utilisée pour initialiser un pointeur vers une fonction membre.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Notes

Les bibliothèques ATL et MFC ont été modifiées pour correspondre à la C++ conformité standard C++ améliorée du compilateur Microsoft. Selon la norme ANSI C++ , la syntaxe d’un pointeur vers une fonction membre de classe doit être `&CMyClass::MyFunc`.

Quand [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) n’est pas défini (cas par défaut), ATL/MFC désactive l’erreur C4867 dans les cartes de macros (notamment les tables des messages) pour que le code créé dans les versions antérieures puisse continuer à être généré comme avant. Si vous définissez **_ATL_ENABLE_PTM_WARNING**, votre code doit être C++ conforme à la norme standard.

Toutefois, le formulaire non standard est déconseillé. Vous devez déplacer le code existant vers C++ une syntaxe conforme standard. Par exemple, le code suivant :

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

Doit être remplacé par:

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

Pour les macros cartographiques, ajoutez le caractère «&». Vous ne devez pas rajouter le caractère dans votre code.

##  <a name="_atl_free_threaded"></a>  _ATL_FREE_THREADED

Définissez si un ou plusieurs de vos objets utilisent le Threading libre ou neutre.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Notes

Spécifie le Threading libre. Le Threading libre est équivalent à un modèle multithread cloisonné. Consultez [spécification du modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour d’autres options de Threading, et [options, Assistant objet simple ATL](../../atl/reference/options-atl-simple-object-wizard.md) pour obtenir une description des modèles de thread disponibles pour un objet ATL.

##  <a name="_atl_multi_threaded"></a>  _ATL_MULTI_THREADED

Symbole qui indique que le projet aura des objets marqués comme étant à la fois, libres ou neutres.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Notes

Si ce symbole est défini, ATL extrait du code qui synchronisera correctement l’accès aux données globales. Le nouveau code doit utiliser la macro [_ATL_FREE_THREADED](#_atl_free_threaded) équivalente à la place.

##  <a name="_atl_no_automatic_namespace"></a>  _ATL_NO_AUTOMATIC_NAMESPACE

Symbole qui empêche l’utilisation par défaut de l’espace de noms comme ATL.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Notes

Si ce symbole n’est pas défini, y compris atlbase. h effectue **l’utilisation d’un espace de noms ATL** par défaut, ce qui peut entraîner des conflits de noms. Pour éviter cela, définissez ce symbole.

##  <a name="_atl_no_com_support"></a>  _ATL_NO_COM_SUPPORT

Symbole qui empêche le code lié à COM d’être compilé avec votre projet.

```
_ATL_NO_COM_SUPPORT
```

##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE

Symbole qui empêche l’initialisation du pointeur vtable dans le constructeur et le destructeur de la classe.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Notes

Si le pointeur vtable ne peut pas être initialisé dans le constructeur et le destructeur de la classe, l’éditeur de liens peut éliminer le vtable et toutes les fonctions vers lesquelles il pointe. Se développe en **_ _ declspec (novtable)** .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

##  <a name="atl_noinline"></a>  ATL_NOINLINE

Symbole qui indique qu’une fonction ne doit pas être Inline.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>Paramètres

*myfunction*<br/>
Fonction qui ne doit pas être Inline.

### <a name="remarks"></a>Notes

Utilisez ce symbole si vous souhaitez vous assurer qu’une fonction n’est pas Inline par le compilateur, même si elle doit être déclarée comme Inline pour pouvoir être placée dans un fichier d’en-tête. Se développe en **_ _ declspec (noinline)** .

##  <a name="_atl_single_threaded"></a>  _ATL_SINGLE_THREADED

Définir si tous vos objets utilisent le modèle de thread unique

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Notes

Spécifie que l’objet s’exécute toujours dans le thread COM principal. Consultez [spécification du modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour d’autres options de Threading, et [options, Assistant objet simple ATL](../../atl/reference/options-atl-simple-object-wizard.md) pour obtenir une description des modèles de thread disponibles pour un objet ATL.

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
