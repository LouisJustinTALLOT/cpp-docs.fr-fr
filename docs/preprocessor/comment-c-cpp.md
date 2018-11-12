---
title: commentaire (C/C++)
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.comment
- comment_CPP
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
ms.openlocfilehash: ec80e8cf177becdc25bdf49d6dfa9ad9c7794b88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612821"
---
# <a name="comment-cc"></a>commentaire (C/C++)

Place un enregistrement de commentaires dans un fichier objet ou un fichier exécutable.

## <a name="syntax"></a>Syntaxe

```
#pragma comment( comment-type [,"commentstring"] )
```

## <a name="remarks"></a>Notes

Le *type commentaire* est un des identificateurs prédéfinis, décrits ci-dessous, qui spécifie le type d’enregistrement de commentaires. Le paramètre facultatif *commentstring* est un littéral de chaîne qui fournit des informations supplémentaires pour certains types de commentaires. Étant donné que *commentstring* est une chaîne littérale, il respecte toutes les règles pour les littéraux de chaîne en ce qui concerne les caractères d’échappement, guillemets incorporés (`"`) et de concaténation.

### <a name="compiler"></a>compilateur

Place le nom et le numéro de version du compilateur dans le fichier objet. Cet enregistrement de commentaires est ignoré par l'Éditeur de liens. Si vous fournissez un *commentstring* paramètre pour ce type d’enregistrement, le compilateur génère un avertissement.

### <a name="exestr"></a>exestr

Emplacements *commentstring* dans le fichier objet. Au moment d'effectuer le lien, cette chaîne est placée dans le fichier exécutable. La chaîne n'est pas chargée en mémoire lorsque le fichier exécutable est chargé. Toutefois, elle peut être détectée à l'aide d'un programme qui recherche les chaînes imprimables dans les fichiers. Ce type d'enregistrement de commentaires peut être utilisé par exemple pour incorporer un numéro de version ou des informations similaires dans un fichier exécutable.

Le mot clé `exestr` est déconseillé et sera supprimé dans une version ultérieure. L'Éditeur de liens ne traite pas l'enregistrement de commentaires.

### <a name="lib"></a>lib

Place un enregistrement de recherche de bibliothèque dans le fichier objet. Ce type de commentaire doit être accompagné par un *commentstring* paramètre qui contient le nom (et éventuellement le chemin d’accès) de la bibliothèque que vous souhaitez que l’éditeur de liens à rechercher. Le nom de la bibliothèque suit les enregistrements de recherche de bibliothèque par défaut dans le fichier objet ; l’éditeur de liens recherche cette bibliothèque comme si vous l’aviez nommée sur la ligne de commande autant que la bibliothèque n’est pas spécifiée avec [/nodefaultlib](../build/reference/nodefaultlib-ignore-libraries.md). Vous pouvez placer plusieurs enregistrements de recherche de bibliothèque dans le même fichier source. Les enregistrements figurent dans le fichier objet dans l'ordre où ils sont rencontrés dans le fichier source.

Si l’ordre de la bibliothèque par défaut et une bibliothèque ajoutée est important, la compilation avec le [/Zl](../build/reference/zl-omit-default-library-name.md) commutateur empêche le nom de bibliothèque par défaut qui est placé dans le module objet. Un deuxième pragma comment peut alors être utilisé pour insérer le nom de la bibliothèque par défaut après la bibliothèque ajoutée. Les bibliothèques répertoriées avec ces pragmas figureront dans le module objet, dans l'ordre où elles sont trouvées dans le code source.

### <a name="linker"></a>éditeur de liens

Place un [option de l’éditeur de liens](../build/reference/linker-options.md) dans le fichier objet. Vous pouvez utiliser ce type-commentaire pour spécifier une option d'éditeur de liens au lieu de la passer à la ligne de commande ou de la spécifier dans l'environnement de développement. Par exemple, vous pouvez spécifier l'option /include pour forcer l'inclusion d'un symbole :

```
#pragma comment(linker, "/include:__mySymbol")
```

Seuls les éléments suivants (*type commentaire*) options de l’éditeur de liens sont disponibles pour être transmis à l’identificateur de l’éditeur de liens :

- [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)

- [/EXPORT](../build/reference/export-exports-a-function.md)

- [/INCLUDE](../build/reference/include-force-symbol-references.md)

- [/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)

- [/MERGE](../build/reference/merge-combine-sections.md)

- [/SECTION](../build/reference/section-specify-section-attributes.md)

### <a name="user"></a>utilisateur

Place un commentaire général dans le fichier objet. Le *commentstring* paramètre contienne le texte du commentaire. Cet enregistrement de commentaires est ignoré par l'Éditeur de liens.

Le pragma ci-dessous indique à l'Éditeur de liens de rechercher la bibliothèque EMAPI.LIB en effectuant la liaison. L'Éditeur de liens commence par rechercher dans le répertoire de travail actuel, puis dans le chemin d'accès spécifié dans la variable d'environnement LIB.

```
#pragma comment( lib, "emapi" )
```

Le pragma ci-dessous indique au compilateur de placer le nom et le numéro de version du compilateur dans le fichier objet :

```
#pragma comment( compiler )
```

> [!NOTE]
> Pour les commentaires qui acceptent un *commentstring* paramètre, vous pouvez utiliser une macro dans n’importe quel endroit où vous utiliseriez un littéral de chaîne, sous réserve que la macro se développe en un littéral de chaîne. Vous pouvez également concaténer toute combinaison de littéraux de chaîne et de macros qui se développent en littéraux de chaîne. Par exemple, l'instruction suivante est acceptable :

```
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)