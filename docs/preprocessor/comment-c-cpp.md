---
title: comment (pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.comment
- comment_CPP
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
ms.openlocfilehash: 3175ad5318bcc6fd9aa6233258ccec9033c89be8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219098"
---
# <a name="comment-pragma"></a>comment (pragma)

Place un enregistrement de commentaires dans un fichier objet ou un fichier exécutable.

## <a name="syntax"></a>Syntaxe

> **#pragma comment (** *Commentaire-type* [ **,** "*Comment-String*"] **)**

## <a name="remarks"></a>Notes

Le *type de commentaire* est l’un des identificateurs prédéfinis, décrits ci-dessous, qui spécifie le type d’enregistrement de commentaire. La *chaîne de commentaire* facultative est un littéral de chaîne qui fournit des informations supplémentaires pour certains types de commentaires. Comme *Comment-String* est un littéral de chaîne, il obéit à toutes les règles pour les littéraux de chaîne en ce qui concerne les caractères`"`d’échappement, les guillemets incorporés () et la concaténation.

### <a name="compiler"></a>compilateur

Place le nom et le numéro de version du compilateur dans le fichier objet. Cet enregistrement de commentaires est ignoré par l'Éditeur de liens. Si vous fournissez un paramètre de *chaîne de commentaire* pour ce type d’enregistrement, le compilateur génère un avertissement.

### <a name="lib"></a>lib

Place un enregistrement de recherche de bibliothèque dans le fichier objet. Ce type de commentaire doit être accompagné d’un paramètre de *chaîne de commentaire* contenant le nom (et éventuellement le chemin d’accès) de la bibliothèque dans laquelle vous souhaitez que l’éditeur de liens recherche. Le nom de la bibliothèque suit les enregistrements de recherche de bibliothèque par défaut dans le fichier objet; l’éditeur de liens recherche cette bibliothèque comme si vous l’aviez nommée sur la ligne de commande, à condition que la bibliothèque ne soit pas spécifiée avec [/NODEFAULTLIB](../build/reference/nodefaultlib-ignore-libraries.md). Vous pouvez placer plusieurs enregistrements de recherche de bibliothèque dans le même fichier source. Les enregistrements figurent dans le fichier objet dans l'ordre où ils sont rencontrés dans le fichier source.

Si l’ordre de la bibliothèque par défaut et d’une bibliothèque ajoutée est important, la compilation avec le commutateur [/zl](../build/reference/zl-omit-default-library-name.md) empêche le nom de la bibliothèque par défaut d’être placé dans le module objet. Un deuxième pragma comment peut alors être utilisé pour insérer le nom de la bibliothèque par défaut après la bibliothèque ajoutée. Les bibliothèques répertoriées avec ces pragmas figureront dans le module objet, dans l'ordre où elles sont trouvées dans le code source.

### <a name="linker"></a>éditeur de liens

Place une [option](../build/reference/linker-options.md) de l’éditeur de liens dans le fichier objet. Vous pouvez utiliser ce type-commentaire pour spécifier une option d'éditeur de liens au lieu de la passer à la ligne de commande ou de la spécifier dans l'environnement de développement. Par exemple, vous pouvez spécifier l'option /include pour forcer l'inclusion d'un symbole :

```C
#pragma comment(linker, "/include:__mySymbol")
```

Seules les options de l’éditeur de liens (*type de commentaire*) suivantes peuvent être passées à l’identificateur de l’éditeur de liens:

- [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)

- [/EXPORT](../build/reference/export-exports-a-function.md)

- [/INCLUDE](../build/reference/include-force-symbol-references.md)

- [/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)

- [/MERGE](../build/reference/merge-combine-sections.md)

- [/SECTION](../build/reference/section-specify-section-attributes.md)

### <a name="user"></a>user

Place un commentaire général dans le fichier objet. Le paramètre de *chaîne de commentaire* contient le texte du commentaire. Cet enregistrement de commentaires est ignoré par l'Éditeur de liens.

## <a name="examples"></a>Exemples

Le pragma ci-dessous indique à l'Éditeur de liens de rechercher la bibliothèque EMAPI.LIB en effectuant la liaison. L'Éditeur de liens commence par rechercher dans le répertoire de travail actuel, puis dans le chemin d'accès spécifié dans la variable d'environnement LIB.

```C
#pragma comment( lib, "emapi" )
```

Le pragma ci-dessous indique au compilateur de placer le nom et le numéro de version du compilateur dans le fichier objet :

```C
#pragma comment( compiler )
```

Pour les commentaires qui acceptent un paramètre de *chaîne de commentaire* , vous pouvez utiliser une macro à n’importe quel endroit où vous utiliseriez un littéral de chaîne, à condition que la macro se développe en un littéral de chaîne. Vous pouvez également concaténer toute combinaison de littéraux de chaîne et de macros qui se développent en littéraux de chaîne. Par exemple, l'instruction suivante est acceptable :

```C
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
