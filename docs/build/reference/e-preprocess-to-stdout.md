---
title: /E (Prétraiter dans stdout)
ms.date: 11/04/2016
f1_keywords:
- /e
helpviewer_keywords:
- -E compiler option [C++]
- /E compiler option [C++]
- preprocessor output, copy to stdout
- preprocessor output
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
ms.openlocfilehash: 892203d300c07711d06cff602128ec6e9ceb351c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504571"
---
# <a name="e-preprocess-to-stdout"></a>/E (Prétraiter dans stdout)

Prétraite les fichiers sources C et C++ et copie les fichiers prétraités sur le périphérique de sortie standard.

## <a name="syntax"></a>Syntaxe

```
/E
```

## <a name="remarks"></a>Notes

Dans ce processus, toutes les directives du préprocesseur sont exécutées, les expansions macro sont effectuées et commentaires sont supprimés. Pour conserver les commentaires dans la sortie prétraitée, utilisez le [/C (conserver les commentaires pendant le prétraitement)](../../build/reference/c-preserve-comments-during-preprocessing.md) option du compilateur également.

**/E** ajoute `#line` directives dans la sortie au début et à la fin de chaque fichier inclus et autour des lignes supprimées par les directives de préprocesseur pour une compilation conditionnelle. Ces directives renumérotent les lignes du fichier prétraité. Par conséquent, erreurs générées pendant les phases ultérieures du traitement désignent les numéros de ligne du fichier source d’origine plutôt que les lignes dans le fichier prétraité.

Le **/E** option supprime la compilation. Vous devez renvoyer le fichier prétraité pour la compilation. **/E** supprime également les fichiers de sortie à partir de la **/FA**, **/Fa**, et **/Fm** options. Pour plus d’informations, consultez [/FA, /Fa (fichier Listing)](../../build/reference/fa-fa-listing-file.md) et [/Fm (nom de fichier de mappage)](../../build/reference/fm-name-mapfile.md).

Pour supprimer `#line` directives, utilisez le [/EP (Prétraiter dans stdout sans directive #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) plutôt l’option.

Pour envoyer la sortie prétraitée dans un fichier plutôt qu’à `stdout`, utilisez le [/P (Prétraiter dans un fichier)](../../build/reference/p-preprocess-to-a-file.md) plutôt l’option.

Pour supprimer `#line` directives et envoyer la sortie prétraitée dans un fichier, utilisez **/P** et **/EP** ensemble.

Vous ne pouvez pas utiliser des en-têtes précompilés avec le **/E** option.

Notez que lors du prétraitement vers un fichier distinct, les espaces ne sont pas émis après les jetons. Cela peut entraîner un programme non conforme ou avoir des effets secondaires involontaires. Le programme suivant se compile correctement :

```
#define m(x) x
m(int)main( )
{
   return 0;
}
```

Toutefois, si vous compilez avec :

```
cl -E test.cpp > test2.cpp
```

`int main` test2.cpp incorrectement seront `intmain`.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l’option du compilateur dans le **des Options supplémentaires**boîte.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Exemple

La ligne de commande suivante prétraite `ADD.C`, conserve les commentaires, ajoute `#line` directives et affiche le résultat sur le périphérique de sortie standard :

```
CL /E /C ADD.C
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)