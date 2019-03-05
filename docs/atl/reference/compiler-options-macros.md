---
title: Macros d’Options de compilateur
ms.date: 11/04/2016
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
ms.openlocfilehash: 79b1cabc0304e905012db5f6dd73ed71073c0c1e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258474"
---
# <a name="compiler-options-macros"></a>Macros d’Options de compilateur

Ces macros contrôlent les fonctionnalités de compilateur spécifique.

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Un symbole qui active les erreurs dans les projets convertis à partir de versions précédentes de l’ATL.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Définir si un ou plusieurs de vos objets utilisent le cloisonnement des threads.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Permet de s’assurer `CString` constructeurs explicites, empêchant toute conversion involontaire.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Définir cette macro pour pouvoir utiliser C++ conforme syntaxe standard, ce qui génère l’erreur du compilateur C4867 lorsqu’une syntaxe non standard est utilisée pour initialiser un pointeur vers une fonction membre.|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Définir si un ou plusieurs de vos objets utilisent de thread libre ou neutre.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Un symbole qui indique le projet aura des objets qui sont marqués comme à la fois, gratuit ou neutre. La macro [_ATL_FREE_THREADED](#_atl_free_threaded) doit être utilisé à la place.|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Un symbole qui empêche l’utilisation de la valeur par défaut de l’espace de noms comme ATL.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Un symbole qui empêche que code lié à COM qui est compilé avec votre projet.|
|[ATL_NO_VTABLE](#atl_no_vtable)|Un symbole qui empêche le pointeur vtable ne soit initialisé dans le constructeur et le destructeur de la classe.|
|[ATL_NOINLINE](#atl_noinline)|Un symbole qui indique une fonction ne doit pas être inline.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Définir si tous vos objets utilisent le modèle de thread unique.|

##  <a name="_atl_all_warnings"></a>  _ATL_ALL_WARNINGS

Un symbole qui active les erreurs dans les projets convertis à partir de versions précédentes de l’ATL.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Notes

Avant Visual C++ .NET 2002, ATL désactivé d’un grand nombre d’avertissements et en les désactiver pour qu’ils s’affichaient jamais dans le code utilisateur. Plus précisément :

- Expression conditionnelle C4127 est une constante

- C4786 'identificateur' : identificateur tronqué à 'nombre' caractères dans les informations de débogage

- Extension non standard C4201 utilisée : struct/union sans nom

- C4103 'nom_fichier' : #pragma pack permet de modifier l’alignement

- C4291 'déclaration' : opérateur delete correspondant est trouvé ; mémoire ne sera pas libérée si l’initialisation lève une exception

- C4268 'identificateur' : 'const' données static/global initialisées avec le constructeur de valeur par défaut généré par le compilateur remplissent l’objet de zéros non significatifs

- Code inaccessible C4702

Dans les projets convertis à partir de versions précédentes, ces avertissements sont toujours désactivées par les en-têtes de bibliothèques.

En ajoutant la ligne suivante au fichier stdafx.h avant d’inclure les en-têtes de bibliothèques, ce comportement peut être modifié.

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

Si cette `#define` est ajoutée, les en-têtes ATL sont faites attention de ne conserver l’état de ces avertissements afin qu’ils ne sont pas désactivés dans le monde entier (ou si l’utilisateur désactive explicitement des avertissements individuels, ne pas pour les activer).

Faire de nouveaux projets `#define` définis dans stdafx.h par défaut.

##  <a name="_atl_apartment_threaded"></a>  _ATL_APARTMENT_THREADED

Définir si un ou plusieurs de vos objets utilisent le cloisonnement des threads.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Notes

Spécifie le modèle de thread cloisonné. Consultez [en spécifiant le modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour d’autres options, de thread et [Options, Assistant objet Simple ATL](../../atl/reference/options-atl-simple-object-wizard.md) pour obtenir une description de la thread les modèles disponibles pour un objet ATL.

##  <a name="_atl_cstring_explicit_constructors"></a>  _ATL_CSTRING_EXPLICIT_CONSTRUCTORS

Permet de s’assurer `CString` constructeurs explicites, empêchant toute conversion involontaire.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Notes

Lorsqu’il est défini, tous les constructeurs CString qui prennent un paramètre unique sont compilées avec le mot clé explicit, ce qui empêche les conversions implicites des arguments d’entrée. Cela signifie, par exemple, que lorsque _UNICODE est défini, si vous essayez d’utiliser une chaîne char * en tant qu’un argument de constructeur CString, entraîne une erreur du compilateur. Utilisez cette macro dans les situations où vous devez empêcher les conversions implicites entre les types de chaîne étroits et larges.

À l’aide de la macro _T sur tous les arguments de chaîne du constructeur, vous pouvez définir _ATL_CSTRING_EXPLICIT_CONSTRUCTORS et éviter les erreurs de compilation que _UNICODE est défini.

##  <a name="_atl_enable_ptm_warning"></a>  _ATL_ENABLE_PTM_WARNING

Définir cette macro afin de forcer l’utilisation de la syntaxe compatible avec la norme ANSI C++ pour les fonctions pointeur vers membre. L’utilisation de cette macro entraîne l’erreur du compilateur C4867 doit être généré lors de la syntaxe non standard est utilisée pour initialiser un pointeur vers une fonction membre.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Notes

Les bibliothèques ATL et MFC ont été modifiés pour correspondre à la conformité de C++ standard améliorée du compilateur Visual C++. Selon la norme ANSI C++, la syntaxe d’un pointeur vers une fonction membre de classe doit être `&CMyClass::MyFunc`.

Lorsque [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) n’est pas défini (le cas par défaut), ATL/MFC désactive l’erreur C4867 dans les mappages de macro (notamment message mappe) afin que le code qui a été créé dans les versions antérieures permettre continuer à créer comme avant. Si vous définissez **_ATL_ENABLE_PTM_WARNING**, votre code doit être conforme à la norme C++.

Toutefois, le formulaire non standard est déprécié, donc vous devez déplacer le code existant à la syntaxe conforme standard C++. Par exemple, ce qui suit :

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

Doit être remplacé par :

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

Notez que pour les macros de mappage qui ajoute le caractère '&', vous ne devez pas l’ajouter à nouveau dans votre code.

##  <a name="_atl_free_threaded"></a>  _ATL_FREE_THREADED

Définir si un ou plusieurs de vos objets utilisent de thread libre ou neutre.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Notes

Spécifie le modèle de thread libre. Ce qui équivaut à un modèle de cloisonnement multithread. Consultez [en spécifiant le modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour d’autres options, de thread et [Options, Assistant objet Simple ATL](../../atl/reference/options-atl-simple-object-wizard.md) pour obtenir une description de la thread les modèles disponibles pour un objet ATL.

##  <a name="_atl_multi_threaded"></a>  _ATL_MULTI_THREADED

Un symbole qui indique le projet aura des objets qui sont marqués comme à la fois, gratuit ou neutre.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Notes

Si ce symbole est défini, ATL extraira dans le code qui va synchroniser correctement les accès aux données globales. Nouveau code doit utiliser la macro équivalente [_ATL_FREE_THREADED](#_atl_free_threaded) à la place.

##  <a name="_atl_no_automatic_namespace"></a>  _ATL_NO_AUTOMATIC_NAMESPACE

Un symbole qui empêche l’utilisation de la valeur par défaut de l’espace de noms comme ATL.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Notes

Si ce symbole n’est pas défini, y compris atlbase.h effectue **à l’aide de l’espace de noms ATL** par défaut, ce qui peut entraîner des conflits de noms. Pour éviter ce problème, définissez ce symbole.

##  <a name="_atl_no_com_support"></a>  _ATL_NO_COM_SUPPORT

Un symbole qui empêche que code lié à COM qui est compilé avec votre projet.

```
_ATL_NO_COM_SUPPORT
```

##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE

Un symbole qui empêche le pointeur vtable ne soit initialisé dans le constructeur et le destructeur de la classe.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Notes

Si le pointeur vtable ne peut pas en cours d’initialisation dans le constructeur de la classe et le destructeur, l’éditeur de liens peut éliminer la vtable et toutes les fonctions vers lequel il pointe. Se développe en **__declspec (novtable)**.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

##  <a name="atl_noinline"></a>  ATL_NOINLINE

Un symbole qui indique une fonction ne doit pas être inline.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>Paramètres

*myfunction*<br/>
La fonction ne doit pas être inline.

### <a name="remarks"></a>Notes

Si vous souhaitez vous assurer qu'une fonction n’obtient pas inline par le compilateur, même si elle doit être déclarée en tant qu’inline afin qu’elle peut être placée dans un fichier d’en-tête d’utiliser ce symbole. Se développe en **noinline**.

##  <a name="_atl_single_threaded"></a>  _ATL_SINGLE_THREADED

Définir si tous vos objets utilisent le modèle de thread unique

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Notes

Spécifie que l’objet s’exécute toujours dans le thread COM principal. Consultez [en spécifiant le modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour d’autres options, de thread et [Options, Assistant objet Simple ATL](../../atl/reference/options-atl-simple-object-wizard.md) pour obtenir une description de la thread les modèles disponibles pour un objet ATL.

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
