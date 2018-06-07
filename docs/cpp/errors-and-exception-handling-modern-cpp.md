---
title: Erreurs et exceptions (Modern C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94a9e75770e822c89ea65a745a2fca491f175d95
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569860"
---
# <a name="errors-and-exception-handling-modern-c"></a>Gestion des erreurs et des exceptions (Modern C++)
En C++ moderne, dans la plupart des scénarios, la meilleure façon de signaler et gérer les erreurs de logique et erreurs d’exécution est d’utiliser des exceptions. Cela est particulièrement vrai lors de la pile peut contenir plusieurs appels de fonction entre la fonction qui détecte l’erreur et la fonction qui a le contexte de savoir comment la gérer. Les exceptions offrent un moyen de formel et bien défini pour le code qui détecte les erreurs pour passer les informations de la pile des appels.  
  
 Erreurs du programme sont généralement répartis en deux catégories : les erreurs de logique provoqués par programmation des erreurs, par exemple, une erreur « index hors limites » et les erreurs d’exécution qui n’entrent pas dans le contrôle du programmeur, par exemple, un « réseau service non disponible » erreur. Dans la programmation de style C et COM, le rapport d’erreurs est géré en retournant une valeur qui représente un code d’erreur ou un code d’état pour une fonction particulière, soit en définissant une variable globale qui l’appelant peut éventuellement récupérer après chaque appel de fonction pour afficher Indique si les erreurs sont signalées. Par exemple, programmation COM utilise la valeur de retour HRESULT pour communiquer des erreurs à l’appelant et l’API Win32 a la fonction GetLastError pour récupérer la dernière erreur a été signalée par la pile des appels. Dans ces deux cas, c’est à l’appelant de reconnaître le code et y répondre convenablement. Si l’appelant ne gère pas explicitement le code d’erreur, le programme peut se bloquer sans avertissement, ou continuer à s’exécuter avec des données incorrectes et produire des résultats incorrects.  
  
 Les exceptions sont préférables en C++ moderne pour les raisons suivantes :  
  
-   Une exception force le code appelant pour reconnaître une condition d’erreur et la gérer. Exceptions non gérées arrêtent l’exécution du programme.  
  
-   Une exception atteint le point dans la pile des appels qui peut gérer l’erreur. Les fonctions intermédiaires peuvent propager l’exception. Ils n’ont pas à coordonner avec les autres couches.  
  
-   Le mécanisme de déroulement de pile d’exception détruit tous les objets dans l’étendue en fonction de règles bien définies après qu’une exception est levée.  
  
-   Une exception permet une séparation nette entre le code qui détecte l’erreur et le code qui gère l’erreur.  
  
 L’exemple simplifié suivant montre la syntaxe nécessaire pour lever et intercepter des exceptions dans C++.  
  
```cpp  
#include <stdexcept>  
#include <limits>  
#include <iostream>  
  
using namespace std;  
class MyClass  
{  
public:  
   void MyFunc(char c)  
   {  
      if(c > numeric_limits<char>::max())  
         throw invalid_argument("MyFunc argument too large.");  
      //...  
   }  
};  
  
int main()  
{  
   try  
   {  
      MyFunc(256); //cause an exception to throw  
   }  
  
   catch(invalid_argument& e)  
   {  
      cerr << e.what() << endl;  
      return -1;  
   }  
   //...  
   return 0;  
}  
  
```  
  
 Exceptions dans C++ ressemblent à celles des langages tels que c# et Java. Dans le `try` bloquer, si une exception est *levée* sera *interceptée* par le premier associé `catch` bloc dont le type correspond à celui de l’exception. En d’autres termes, l’exécution passe à partir de la `throw` instruction à la `catch` instruction. Si aucun bloc catch utilisable n’est trouvée, `std::terminate` est appelée et le programme se termine. En C++, n’importe quel type peut être levé ; Toutefois, nous vous recommandons de lever un type qui dérive directement ou indirectement de `std::exception`. Dans l’exemple précédent, le type d’exception, [invalid_argument](../standard-library/invalid-argument-class.md), est défini dans la bibliothèque standard dans le [ \<stdexcept >](../standard-library/stdexcept.md) fichier d’en-tête. C++ ne fournit pas et ne requiert pas, un `finally` bloc pour vous assurer que toutes les ressources sont libérées si une exception est levée. L’acquisition de ressources est l’idiome RAII (initialization), qui utilise des pointeurs intelligents, fournit les fonctionnalités requises pour le nettoyage des ressources. Pour plus d’informations, consultez [Comment : conception pour la sécurité des exceptions](../cpp/how-to-design-for-exception-safety.md). Pour plus d’informations sur le mécanisme de déroulement de pile C++, consultez [Exceptions et déroulement de pile](../cpp/exceptions-and-stack-unwinding-in-cpp.md).  
  
## <a name="basic-guidelines"></a>Recommandations de base  
 Gestion des erreurs fiable sont importante dans n’importe quel langage de programmation. Bien que les exceptions fournissent plusieurs fonctionnalités qui prennent en charge la gestion des erreurs de bonnes, ils ne peuvent pas effectuer tout le travail pour vous. Pour profiter des avantages du mécanisme d’exception, empêchent les exceptions à l’esprit lorsque vous concevez votre code.  
  
-   Utilisez les assertions pour rechercher les erreurs qui ne doivent jamais se produire. Utiliser des exceptions pour rechercher les erreurs qui peuvent se produire, par exemple, les erreurs de validation des entrées sur les paramètres de fonctions publiques. Pour plus d’informations, consultez la section intitulée **vs d’Exceptions. Assertions**.  
  
-   Utiliser des exceptions lorsque le code qui gère l’erreur peut être séparé par un ou plusieurs appels de fonction qui interviennent à partir du code qui détecte l’erreur. Pensez à utiliser à la place des codes d’erreur dans les boucles critique pour les performances lorsque le code qui gère l’erreur est étroitement lié au code qui détecte. 
  
-   Pour chaque fonction qui peut lever ou propage une exception, fournir parmi les trois garanties d’exception : la garantie forte, la garantie de base ou la garantie nothrow (noexcept). Pour plus d’informations, consultez [Comment : conception pour la sécurité des exceptions](../cpp/how-to-design-for-exception-safety.md).  
  
-   Lever des exceptions par valeur, les intercepter par référence. Ne pas intercepter ne peut pas traiter. 
  
-   N’utilisez pas les spécifications d’exceptions, qui sont déconseillées dans C ++ 11. Pour plus d’informations, consultez la section intitulée **spécifications d’Exception et noexcept**.  
  
-   Utilisez les types d’exception de bibliothèque standard lorsqu’elles s’appliquent. Dériver des types d’exception personnalisés à partir de la [exception, classe](../standard-library/exception-class.md) hiérarchie.  
  
-   Ne pas autoriser les exceptions à la séquence d’échappement de destructeurs ou de fonctions de désallocation de mémoire.  
  
## <a name="exceptions-and-performance"></a>Exceptions et performances  
 Le mécanisme d’exception a un impact si aucune exception n’est levée sur les performances très minimes. Si une exception est levée, le coût du parcours de pile et déroulement sont comparable à peu près au coût d’un appel de fonction. Structures de données supplémentaires sont nécessaires pour effectuer le suivi de la pile des appels après un `try` bloc est entré, et des instructions supplémentaires sont nécessaires au déroulement de la pile si une exception est levée. Toutefois, dans la plupart des scénarios, le coût de performances et l’encombrement mémoire n’est pas significatif. L’effet négatif d’exceptions sur les performances est susceptible d’être significatifs uniquement sur les systèmes très limité en mémoire ou dans performances critiques effectue une itération dans laquelle une erreur est susceptible de se produire régulièrement et le code de gestion qu’il est étroitement lié au code qui signale. Dans tous les cas, il est impossible de connaître le coût réel des exceptions sans profilage et de mesure. Même dans les rares cas lorsque le coût est élevé, vous pouvez le peser par rapport à d’autres avantages fournis par une stratégie de l’exception bien conçue, facilité de maintenance plus facile et l’exactitude des.  
  
## <a name="exceptions-vs-assertions"></a>Exceptions et les assertions  
 Exceptions et les assertions sont deux mécanismes distincts pour la détection des erreurs d’exécution dans un programme. Utilisation d’assertions pour tester des conditions pendant le développement ne doit jamais être true si l’ensemble de votre code est correct. Il n’existe aucun point de gestion de cette erreur à l’aide d’une exception, car l’erreur indique qu’un élément dans le code doit être résolu et ne représente pas une condition que le programme doit récupérer à partir de l’exécution. Une assertion s’arrête l’exécution à l’instruction afin que vous pouvez inspecter l’état du programme dans le débogueur ; une exception poursuit l’exécution à partir du premier gestionnaire catch appropriée. Utiliser des exceptions pour vérifier les conditions d’erreur qui peuvent se produire au moment de l’exécution, même si votre code est correct, par exemple, « fichier introuvable » ou « mémoire insuffisante. » Vous pouvez souhaiter récupérer à partir de ces conditions, même si la récupération simplement génère un message dans un journal et termine le programme. Vérifiez toujours les arguments des fonctions publiques à l’aide des exceptions. Même si votre fonction est sans erreur, vous n’avez ne peut-être pas de contrôle total sur les arguments qui lui peut passer un utilisateur.  
  
## <a name="c-exceptions-versus-windows-seh-exceptions"></a>Exceptions C++ et les exceptions SEH de Windows  
 Les programmes C et C++ peuvent utiliser la mécanisme (SEH) dans le système d’exploitation de gestion structurée des exceptions. Les concepts de gestion des exceptions structurées ressemblent à celles des exceptions C++, mais SEH utilise le `__try`, `__except`, et `__finally` construit à la place de `try` et `catch`. Dans Visual C++, les exceptions C++ sont implémentées pour la gestion structurée des exceptions. Toutefois, lorsque vous écrivez du code C++, utilisez la syntaxe d’exception C++.  
  
 Pour plus d’informations sur la gestion structurée des exceptions, consultez [gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md).  
  
## <a name="exception-specifications-and-noexcept"></a>Noexcept et spécifications d’exception  
 Les spécifications d’exceptions ont été introduites dans C++ comme un moyen de spécifier une fonction peut lever les exceptions. Toutefois, les spécifications d’exceptions a été identifié comme problématiques dans la pratique et sont déconseillées dans la norme C ++ 11 brouillon. Nous vous recommandons de ne pas utiliser les spécifications d’exceptions à l’exception de `throw()`, ce qui signifie que la fonction n’autorise aucune exception d’échapper. Si vous devez utiliser des spécifications d’exception du type `throw(` *type*`)`, gardez à l’esprit que Visual C++ s’éloigne de la norme de certaines façons. Pour plus d’informations, consultez [spécifications d’Exception (throw)](../cpp/exception-specifications-throw-cpp.md). Le `noexcept` spécificateur est introduit dans C ++ 11 comme alternative pour `throw()`.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : Interface entre le Code exceptionnel et Non exceptionnel](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)   
 [Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Référence du langage C++](../cpp/cpp-language-reference.md)   
 [Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
