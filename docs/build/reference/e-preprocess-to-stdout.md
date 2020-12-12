---
description: En savoir plus sur:/E (Prétraiter dans stdout)
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
ms.openlocfilehash: 9d6c9ea3a5fcf8e7ba06ede6e7e70d933b5c921a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192603"
---
# <a name="e-preprocess-to-stdout"></a>/E (Prétraiter dans stdout)

Prétraite les fichiers sources C et C++ et copie les fichiers prétraités sur le périphérique de sortie standard.

## <a name="syntax"></a>Syntaxe

```
/E
```

## <a name="remarks"></a>Notes

Dans ce processus, toutes les directives de préprocesseur sont exécutées, les expansions de macro sont effectuées et les commentaires sont supprimés. Pour conserver les commentaires dans la sortie prétraitée, utilisez également l’option de compilateur [/c (conserver les commentaires pendant le prétraitement)](c-preserve-comments-during-preprocessing.md) .

**/E** ajoute `#line` des directives à la sortie au début et à la fin de chaque fichier inclus et autour des lignes supprimées par les directives de préprocesseur pour la compilation conditionnelle. Ces directives renumérotent les lignes du fichier prétraité. Par conséquent, les erreurs générées lors des étapes ultérieures de traitement font référence aux numéros de ligne du fichier source d’origine plutôt qu’aux lignes du fichier prétraité.

L’option **/e** supprime la compilation. Vous devez soumettre à nouveau le fichier prétraité pour la compilation. **/E** supprime également les fichiers de sortie des options **/FA**, **/FA** et **/FM** . Pour plus d’informations, consultez [/FA,/FA (liste de fichiers)](fa-fa-listing-file.md) et [/FM (nom de fichier de mappage)](fm-name-mapfile.md).

Pour supprimer `#line` des directives, utilisez plutôt l’option [/EP (Prétraiter dans stdout sans directives #line)](ep-preprocess-to-stdout-without-hash-line-directives.md) .

Pour envoyer la sortie prétraitée à un fichier plutôt qu’à `stdout` , utilisez l’option [/p (Prétraiter dans un fichier)](p-preprocess-to-a-file.md) à la place.

Pour supprimer des `#line` directives et envoyer la sortie prétraitée à un fichier, utilisez **/P** et **/EP** ensemble.

Vous ne pouvez pas utiliser d’en-têtes précompilés avec l’option **/e** .

Notez qu’en cas de prétraitement dans un fichier distinct, les espaces ne sont pas émis après les jetons. Cela peut entraîner un programme illégal ou avoir des effets secondaires inattendus. Le programme suivant compile correctement :

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

`int main` dans test2. cpp, est incorrect `intmain` .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l’option de compilateur dans la zone **options supplémentaires**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Exemple

La ligne de commande suivante prétraite `ADD.C` , conserve les commentaires, ajoute des `#line` directives et affiche le résultat sur le périphérique de sortie standard :

```
CL /E /C ADD.C
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
