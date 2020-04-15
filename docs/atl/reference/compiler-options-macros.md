---
title: Macros Options Compilateur
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
ms.openlocfilehash: 702324c3300ff23bb60113529a681e3b8fa99354
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331619"
---
# <a name="compiler-options-macros"></a>Macros Options Compilateur

Ces macros contrôlent des caractéristiques spécifiques de compilateur.

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Un symbole qui permet des erreurs dans les projets convertis à partir des versions précédentes d’ATL.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Définissez si un ou plusieurs de vos objets utilisent le threading d’appartement.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Rend `CString` certains constructeurs explicites, empêchant toute conversion involontaire.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Définissez cette macro afin d’utiliser la syntaxe conforme à la norme CMD, qui génère l’erreur de compilateur C4867 lorsqu’une syntaxe non standard est utilisée pour initialiser un pointeur sur une fonction de membre.|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Définissez si un ou plusieurs de vos objets utilisent un threading gratuit ou neutre.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Un symbole qui indique que le projet aura des objets qui sont marqués comme les deux, libres ou neutres. Le macro [_ATL_FREE_THREADED](#_atl_free_threaded) devrait être utilisé à la place.|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Un symbole qui empêche l’utilisation par défaut de namespace comme ATL.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Un symbole qui empêche le code COM d’être compilé avec votre projet.|
|[ATL_NO_VTABLE](#atl_no_vtable)|Un symbole qui empêche le pointeur vtable d’être initialisé dans le constructeur et le destructeur de la classe.|
|[ATL_NOINLINE](#atl_noinline)|Un symbole qui indique qu’une fonction ne doit pas être inlinée.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Définissez si tous vos objets utilisent le modèle de threading unique.|

## <a name="_atl_all_warnings"></a><a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS

Un symbole qui permet des erreurs dans les projets convertis à partir des versions précédentes d’ATL.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Notes

Avant Visual C .NET 2002, ATL désactivé de nombreux avertissements et les a laissés désactivés de sorte qu’ils ne sont jamais apparus dans le code utilisateur. Plus précisément :

- L’expression conditionnelle C4127 est constante

- C4786 'identifiant' : l’identifiant a été tronqué pour 'numéror' des caractères dans les informations de déboiffées

- C4201 extension non standard utilisée : struct/union sans nom

- C4103 'filename' : pack #pragma utilisé pour changer d’alignement

- C4291 'déclaration' : aucun opérateur correspondant supprimé trouvé; mémoire ne sera pas libérée si l’initialisation jette une exception

- C4268 'identifiant' : 'const' données statiques/globales paraprimées avec un constructeur par défaut généré par compilateur remplit l’objet de zéros

- Code inaccessible C4702

Dans les projets convertis à partir des versions précédentes, ces avertissements sont encore désactivés par les en-têtes des bibliothèques.

En ajoutant la ligne suivante au fichier *pch.h* *(stdafx.h* dans Visual Studio 2017 et plus tôt) avant d’inclure les en-têtes des bibliothèques, ce comportement peut être modifié.

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

Si `#define` cela est ajouté, les en-têtes ATL prennent soin de préserver l’état de ces avertissements afin qu’ils ne soient pas désactivés à l’échelle mondiale (ou si l’utilisateur désactive explicitement les avertissements individuels, pas pour les activer).

De nouveaux `#define` projets ont cet ensemble en *pch.h* (*stdafx.h* dans Visual Studio 2017 et plus tôt) par défaut.

## <a name="_atl_apartment_threaded"></a><a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED

Définissez si un ou plusieurs de vos objets utilisent le threading d’appartement.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Notes

Spécifie le filetage d’appartement. Voir [Spécifier le modèle de threading du projet pour d’autres](../../atl/specifying-the-threading-model-for-a-project-atl.md) options de threading, et [options, ATL Simple Object Wizard](../../atl/reference/options-atl-simple-object-wizard.md) pour une description des modèles de threading disponibles pour un objet ATL.

## <a name="_atl_cstring_explicit_constructors"></a><a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS

Rend `CString` certains constructeurs explicites, empêchant toute conversion involontaire.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Notes

Lorsque ce constructeur est défini, tous les constructeurs CString qui prennent un seul paramètre sont compilés avec le mot clé explicite, ce qui empêche les conversions implicites d’arguments d’entrée. Cela signifie, par exemple, que lorsque _UNICODE est définie, si vous essayez d’utiliser une chaîne de charMD comme argument de constructeur CString, une erreur de compilateur en résultera. Utilisez cette macro dans les situations où vous devez empêcher les conversions implicites entre les types de cordes étroites et larges.

En utilisant la macro _T sur tous les arguments de chaîne de constructeurs, vous pouvez définir _ATL_CSTRING_EXPLICIT_CONSTRUCTORS et éviter les erreurs de compilation indépendamment du fait que _UNICODE est défini.

## <a name="_atl_enable_ptm_warning"></a><a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING

Définissez cette macro afin de forcer l’utilisation de la syntaxe standard-conforme ANSI CMD pour pointer vers les fonctions des membres. L’utilisation de cette macro entraînera l’erreur de compilateur C4867 à générer lorsque la syntaxe non standard est utilisée pour initialiser un pointeur à une fonction de membre.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Notes

Les bibliothèques ATL et MFC ont été modifiées pour correspondre à la conformité standard améliorée du compilateur Microsoft CMD. Selon la norme ANSI C, la syntaxe d’un pointeur à une fonction de membre de classe devrait être `&CMyClass::MyFunc`.

Lorsque [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) n’est pas définie (le cas par défaut), ATL/MFC désactive l’erreur C4867 dans les cartes macro (notamment les cartes de messages) de sorte que le code qui a été créé dans les versions antérieures peut continuer à construire comme avant. Si vous définissez **_ATL_ENABLE_PTM_WARNING,** votre code doit être conforme à la norme C.

Cependant, le formulaire non standard a été déprécié. Vous devez déplacer le code existant vers la syntaxe conforme à la norme C. Par exemple, le code suivant :

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

Doit être remplacé par :

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

Pour les macros de carte, ajoutez le caractère ampersand '&'. Vous ne devriez pas ajouter le personnage à nouveau dans votre code.

## <a name="_atl_free_threaded"></a><a name="_atl_free_threaded"></a>_ATL_FREE_THREADED

Définissez si un ou plusieurs de vos objets utilisent un threading gratuit ou neutre.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Notes

Spécifie le threading gratuit. Le filetage gratuit équivaut à un modèle d’appartement multitâli. Voir [Spécifier le modèle de threading du projet pour d’autres](../../atl/specifying-the-threading-model-for-a-project-atl.md) options de threading, et [options, ATL Simple Object Wizard](../../atl/reference/options-atl-simple-object-wizard.md) pour une description des modèles de threading disponibles pour un objet ATL.

## <a name="_atl_multi_threaded"></a><a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED

Un symbole qui indique que le projet aura des objets qui sont marqués comme les deux, libres ou neutres.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Notes

Si ce symbole est défini, ATL va extraire du code qui synchronisera correctement l’accès aux données mondiales. Le nouveau code devrait utiliser la macro [équivalente _ATL_FREE_THREADED](#_atl_free_threaded) à la place.

## <a name="_atl_no_automatic_namespace"></a><a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE

Un symbole qui empêche l’utilisation par défaut de namespace comme ATL.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Notes

Si ce symbole n’est pas défini, y compris atlbase.h effectuera **en utilisant l’espace nom ATL** par défaut, ce qui peut conduire à des conflits de nommage. Pour éviter cela, définissez ce symbole.

## <a name="_atl_no_com_support"></a><a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT

Un symbole qui empêche le code COM d’être compilé avec votre projet.

```
_ATL_NO_COM_SUPPORT
```

## <a name="atl_no_vtable"></a><a name="atl_no_vtable"></a>ATL_NO_VTABLE

Un symbole qui empêche le pointeur vtable d’être initialisé dans le constructeur et le destructeur de la classe.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Notes

Si le pointeur vtable est empêché d’être paralysé dans le constructeur et le destructeur de la classe, le lien peut éliminer le vtable et toutes les fonctions auxquelles il pointe. S’étend à **__declspec (novtable)**.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

## <a name="atl_noinline"></a><a name="atl_noinline"></a>ATL_NOINLINE

Un symbole qui indique qu’une fonction ne doit pas être inlinée.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>Paramètres

*myfonction*<br/>
La fonction qui ne doit pas être inlinisée.

### <a name="remarks"></a>Notes

Utilisez ce symbole si vous voulez vous assurer qu’une fonction ne se fait pas inlinisé par le compilateur, même si elle doit être déclarée en ligne afin qu’elle puisse être placée dans un fichier d’en-tête. S’étend à **__declspec (noinline)**.

## <a name="_atl_single_threaded"></a><a name="_atl_single_threaded"></a>_ATL_SINGLE_THREADED

Définissez si tous vos objets utilisent le modèle de threading unique

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Notes

Spécifie que l’objet s’exécute toujours dans le fil COM primaire. Voir [Spécifier le modèle de threading du projet pour d’autres](../../atl/specifying-the-threading-model-for-a-project-atl.md) options de threading, et [options, ATL Simple Object Wizard](../../atl/reference/options-atl-simple-object-wizard.md) pour une description des modèles de threading disponibles pour un objet ATL.

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
