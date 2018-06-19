---
title: Plateforme, par défaut et cli espaces de noms (Extensions du composant C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- lang
- cli
dev_langs:
- C++
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b466a94aba9f19907a5438a8b8e623d65aa0ac2d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880739"
---
# <a name="platform-default-and-cli-namespaces--c-component-extensions"></a>Plateforme, valeurs par défaut et espaces de noms CLI (extensions du composant C++)
Un espace de noms qualifie les noms des éléments du langage afin que les noms n'entrent pas en conflit avec des noms sinon identiques ailleurs dans le code source. Par exemple, une collision de nom peut empêcher le compilateur de reconnaître [mots clés contextuels](../windows/context-sensitive-keywords-cpp-component-extensions.md). Les espaces de noms sont utilisés par le compilateur mais ne sont pas conservés dans l'assembly compilé.  
  
## <a name="all-runtimes"></a>Tous les runtimes  
 Visual C++ offre un espace de noms par défaut pour votre projet lorsque vous créez le projet. Vous pouvez renommer manuellement l’espace de noms, bien que dans Windows Runtime, le nom du fichier .winmd doit correspondre au nom de l’espace de noms racine.  
  
## <a name="windows-runtime"></a>Windows Runtime  
 Pour plus d’informations, consultez [espaces de noms et le type de visibilité (C + c++ / CX)](http://msdn.microsoft.com/library/windows/apps/hh969551.aspx).  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **Syntaxe**  
  
```  
using namespace cli;  
```  
  
 **Remarques**  
  
 C + c++ / CLI prend en charge la `cli` espace de noms. Lors de la compilation avec **/CLR**, la `using` instruction dans la section syntaxe est implicite.  
  
 Les fonctionnalités de langage suivantes se trouvent dans l'espace de noms `cli` :  
  
-   [Tableaux](../windows/arrays-cpp-component-extensions.md)  
  
-   [interior_ptr (C++-CLI)](../windows/interior-ptr-cpp-cli.md)  
  
-   [pin_ptr (C++-CLI)](../windows/pin-ptr-cpp-cli.md)  
  
-   [safe_cast](../windows/safe-cast-cpp-component-extensions.md)  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/clr**  
  
### <a name="examples"></a>Exemples  
 **Exemple**  
  
 L'exemple de code suivant montre qu'il est possible d'utiliser un symbole dans l'espace de noms `cli` comme symbole défini par l'utilisateur dans votre code.  Toutefois, une fois que vous l'avez fait, vous devez qualifier explicitement ou implicitement vos références à l'élément de langage `cli` du même nom.  
  
```  
// cli_namespace.cpp  
// compile with: /clr  
using namespace cli;  
int main() {  
   array<int> ^ MyArray = gcnew array<int>(100);  
   int array = 0;  
  
   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062  
  
   // OK  
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);  
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)