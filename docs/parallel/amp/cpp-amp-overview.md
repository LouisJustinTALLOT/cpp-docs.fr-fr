---
title: Présentation de C++ AMP | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, requirements
- C++ Accelerated Massive Parallelism, architecture
- C++ AMP
- C++ Accelerated Massive Parallelism, overview
- C++ Accelerated Massive Parallelism
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8de31ab9009a84c04e594837a0c4fbf30758fea
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694626"
---
# <a name="c-amp-overview"></a>Présentation de C++ AMP
C++ Accelerated les Massive Parallelism (C++ AMP) accélère l’exécution de code C++ en tirant parti du matériel parallèle de données comme une unité de traitement graphique (GPU) sur une carte graphique distincte. À l’aide de C++ AMP, vous pouvez coder les algorithmes de données multidimensionnel afin que l’exécution peut être accélérée à l’aide de parallélisme sur du matériel hétérogène. Le modèle de programmation C++ AMP comprend des tableaux multidimensionnels, l’indexation, le transfert mémoire, la mosaïque et une bibliothèque de fonctions mathématiques. Vous pouvez utiliser les extensions de langage C++ AMP pour contrôler comment les données sont déplacées de l’unité centrale vers la GPU et vice-versa, afin que vous pouvez améliorer les performances.  
  
## <a name="system-requirements"></a>Configuration système requise  
  
- [!INCLUDE[win7](../../build/includes/win7_md.md)], [!INCLUDE[win8](../../build/reference/includes/win8_md.md)], [!INCLUDE[winsvr08_r2](../../parallel/amp/includes/winsvr08_r2_md.md)] ou [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)]  
  
-   DirectX 11 fonctionnalité niveau 11.0 ou composants  
  
-   Pour le débogage sur l’émulateur de logiciel, [!INCLUDE[win8](../../build/reference/includes/win8_md.md)] ou [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)] est requis. Pour effectuer un débogage sur le matériel, vous devez installer les pilotes de votre carte graphique. Pour plus d’informations, consultez [débogage du Code GPU](/visualstudio/debugger/debugging-gpu-code).  
  
## <a name="introduction"></a>Introduction  
 Les deux exemples suivants illustrent les composants principaux de C++ AMP. Supposons que vous voulez ajouter les éléments correspondants de deux tableaux unidimensionnels. Par exemple, vous pouvez souhaiter ajouter `{1, 2, 3, 4, 5}` et `{6, 7, 8, 9, 10}` pour obtenir `{7, 9, 11, 13, 15}`. Sans l’utilisation de C++ AMP, vous pouvez écrire le code suivant pour ajouter les nombres et afficher les résultats.  
  
```cpp  
#include <iostream>  
  
void StandardMethod() {  
  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
  
    for (int idx = 0; idx < 5; idx++)  
    {  
        sumCPP[idx] = aCPP[idx] + bCPP[idx];  
    }  
  
    for (int idx = 0; idx < 5; idx++)  
    {  
        std::cout << sumCPP[idx] << "\n";  
    }  
}  
  
```  
  
 Les parties importantes du code sont les suivantes :  
  
-   Données : Les données se comprennent de trois tableaux. Tous les ont le même rang (un) et la même longueur (5).  
  
-   Itération : La première `for` boucle fournit un mécanisme pour effectuer une itération au sein des éléments dans les tableaux. Le code que vous souhaitez exécuter pour calculer la somme est contenu dans la première `for` bloc.  
  
-   Index : Le `idx` variable accède aux éléments individuels des tableaux.  
  
 À l’aide de C++ AMP, vous pouvez écrire le code suivant à la place.  
  
```cpp  
#include <amp.h>  
#include <iostream>  
using namespace concurrency;  
  
const int size = 5;  
  
void CppAmpMethod() {  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[size];  
  
    // Create C++ AMP objects.  
    array_view<const int, 1> a(size, aCPP);  
    array_view<const int, 1> b(size, bCPP);  
    array_view<int, 1> sum(size, sumCPP);  
    sum.discard_data();  
  
    parallel_for_each(   
        // Define the compute domain, which is the set of threads that are created.  
        sum.extent,   
        // Define the code to run on each thread on the accelerator.  
        [=](index<1> idx) restrict(amp) {  
            sum[idx] = a[idx] + b[idx];  
        }  
    );  
  
    // Print the results. The expected output is "7, 9, 11, 13, 15".  
    for (int i = 0; i < size; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
```  
  
 Les mêmes éléments de base sont présents, mais les constructions C++ AMP sont utilisées :  
  
-   Données : Vous utilisez des tableaux C++ pour construire des trois C++ AMP [array_view](../../parallel/amp/reference/array-view-class.md) objets. Vous fournissez des quatre valeurs pour construire une `array_view` objet : les valeurs de données, le classement, le type d’élément et la longueur de la `array_view` objet dans chaque dimension. Le rang et le type sont passés comme paramètres de type. Les données et la longueur sont passés comme paramètres du constructeur. Dans cet exemple, le tableau de C++ qui est passé au constructeur est unidimensionnel. Le rang et la longueur sont utilisés pour construire la forme rectangulaire de données dans le `array_view` objet et les valeurs sont utilisées pour remplir le tableau de données. La bibliothèque runtime inclut également le [array, classe](../../parallel/amp/reference/array-class.md), qui a une interface qui ressemble à la `array_view` classe et est décrite plus loin dans cet article.  
  
-   Itération : Le [parallel_for_each, fonction (C++ AMP)](reference/concurrency-namespace-functions-amp.md#parallel_for_each) fournit un mécanisme pour l’itération sur les éléments de données, ou *domaine de calcul*. Dans cet exemple, le domaine de calcul est spécifié par `sum.extent`. Le code que vous souhaitez exécuter est contenu dans une expression lambda, ou *fonction noyau*. La `restrict(amp)` indique que seul le sous-ensemble de langage C++ que C++ AMP peut accélérer est utilisé.  
  
-   Index : Le [index, classe](../../parallel/amp/reference/index-class.md) variable, `idx`, est déclaré avec un rang un pour faire correspondre le classement de la `array_view` objet. À l’aide de l’index, vous pouvez accéder à des éléments individuels du `array_view` objets.  
  
## <a name="shaping-and-indexing-data-index-and-extent"></a>Les données de mise en formes et d’indexation : index et l’étendue  
 Vous devez définir les valeurs de données et déclarer la forme des données avant de pouvoir exécuter le code de noyau. Toutes les données est défini comme un tableau (rectangulaire), et vous pouvez définir le tableau pour avoir un rang (nombre de dimensions). Les données peuvent être n’importe quelle taille dans une des dimensions.  
  
### <a name="index-class"></a>index, classe  
 Le [index, classe](../../parallel/amp/reference/index-class.md) spécifie un emplacement dans le `array` ou `array_view` objet en encapsulant l’offset à partir de l’origine dans chaque dimension dans un seul objet. Lorsque vous accédez à un emplacement dans le tableau, vous passez un `index` objet à l’opérateur d’indexation, `[]`, au lieu d’une liste des index d’entiers. Vous pouvez accéder aux éléments dans chaque dimension à l’aide de la [Array::operator opérateur](reference/array-class.md#operator_call) ou [array_view::operator() opérateur](reference/array-view-class.md#operator_call).  
  
 L’exemple suivant crée un index unidimensionnel qui spécifie le troisième élément dans une dimension `array_view` objet. L’index est utilisé pour imprimer le troisième élément de la `array_view` objet. La sortie est 3.  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5};  
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";    
// Output: 3  
```  
  
 L’exemple suivant crée un index à deux dimensions qui spécifie l’élément où la ligne = 1 et la colonne = 2 une à deux dimensions `array_view` objet. Le premier paramètre dans la `index` constructeur est le composant de la ligne, et le deuxième paramètre est le composant de la colonne. La sortie est 6.  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5, 6};  
array_view<int, 2> a(2, 3, aCPP);  
  
index<2> idx(1, 2);  
  
std::cout <<a[idx] << "\n";    
// Output: 6  
```  
  
 L’exemple suivant crée un index en trois dimensions qui spécifie l’élément où la profondeur = 0, la ligne = 1 et la colonne = 3 dans un graphique en trois dimensions `array_view` objet. Notez que le premier paramètre est le composant de profondeur et le deuxième paramètre est le composant de la ligne, et le troisième paramètre est le composant de la colonne. La sortie est 8.  
  
```cpp  
int aCPP[] = {  
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,   
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};  
 
array_view<int, 3> a(2, 3, 4, aCPP);

// Specifies the element at 3, 1, 0.  
index<3> idx(0, 1, 3);

std::cout << a[idx] << "\n";  
// Output: 8  
```  
  
### <a name="extent-class"></a>extent, classe  
 Le [extent, classe](../../parallel/amp/reference/extent-class.md) spécifie la longueur des données dans chaque dimension de la `array` ou `array_view` objet. Vous pouvez créer une mesure et l’utiliser pour créer un `array` ou `array_view` objet. Vous pouvez également récupérer l’étendue d’un objet `array` ou `array_view` objet. L’exemple suivant imprime la longueur de l’extension de chaque dimension d’un `array_view` objet.  
  
```cpp  
int aCPP[] = {  
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,   
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};  
// There are 3 rows and 4 columns, and the depth is two.  
array_view<int, 3> a(2, 3, 4, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";  
std::cout << "The number of rows is " << a.extent[1] << "\n";  
std::cout << "The depth is " << a.extent[0] << "\n";  
std::cout << "Length in most significant dimension is " << a.extent[0] << "\n";  
```  
  
 L’exemple suivant crée un `array_view` objet qui a les mêmes dimensions en tant que l’objet dans l’exemple précédent, mais cet exemple utilise une `extent` objet au lieu d’utiliser des paramètres explicites dans le `array_view` constructeur.  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};  
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";  
std::cout << "The number of rows is " << a.extent[1] << "\n";  
std::cout << "The depth is " << a.extent[0] << "\n";  
```  
  
## <a name="moving-data-to-the-accelerator-array-and-arrayview"></a>Déplacement des données pour l’accélérateur : tableau et array_view  
 Deux conteneurs de données utilisés pour déplacer des données vers l’accélérateur sont définies dans la bibliothèque runtime. Ils sont le [array, classe](../../parallel/amp/reference/array-class.md) et [array_view, classe](../../parallel/amp/reference/array-view-class.md). Le `array` est une classe de conteneur qui crée une copie complète des données lorsque l’objet est construit. Le `array_view` est une classe de wrapper qui copie les données lors de la fonction noyau accède aux données. Lorsque les données sont requises sur le périphérique source les données sont copiées en retour.  
  
### <a name="array-class"></a>array, classe  
 Lorsqu’un `array` objet est construit, une copie complète des données est créée sur l’accélérateur si vous utilisez un constructeur qui inclut un pointeur vers le jeu de données. La fonction noyau modifie la copie de l’accélérateur. Lorsque l’exécution de la fonction noyau est terminée, vous devez copier les données vers la structure de données source. L’exemple suivant multiplie chaque élément dans un vecteur par 10. Une fois la fonction noyau est terminée, le `vector conversion operator` est utilisé pour copier les données dans l’objet vector.  
  
```cpp  
std::vector<int> data(5);

for (int count = 0; count <5; count++)   
{  
    data[count] = count;  
}  
 
array<int, 1> a(5, data.begin(), data.end());
 
parallel_for_each(
    a.extent, 
    [=, &a](index<1> idx) restrict(amp) {  
        a[idx] = a[idx]* 10;  
    });
  
data = a;  
for (int i = 0; i < 5; i++)   
{  
    std::cout << data[i] << "\n";  
}  
```  
  
### <a name="arrayview-class"></a>array_view, classe  
 Le `array_view` a presque les mêmes membres que la `array` classe, mais le comportement sous-jacent n’est pas le même. Données passées à la `array_view` constructeur n’est pas répliqué sur le GPU qu’avec un `array` constructeur. Au lieu de cela, les données sont copiées à l’accélérateur lors de l’exécution de la fonction de noyau. Par conséquent, si vous créez deux `array_view` les objets qui utilisent les mêmes données, les deux `array_view` objets font référence au même espace mémoire. Lorsque vous faites cela, vous devez synchroniser l’accès multithread. Le principal avantage de l’utilisation de la `array_view` classe est que les données sont déplacées uniquement s’il est nécessaire.  
  
### <a name="comparison-of-array-and-arrayview"></a>Comparaison du tableau et array_view  
 Le tableau suivant résume les similitudes et différences entre les `array` et `array_view` classes.  
  
|Description|array (classe)|array_view (classe)|  
|-----------------|-----------------|-----------------------|  
|Lorsque le rang est déterminé|Au moment de la compilation.|Au moment de la compilation.|  
|Lorsque la mesure est déterminé|Au moment de l’exécution.|Au moment de l’exécution.|  
|Forme|Rectangulaire.|Rectangulaire.|  
|Stockage de données|Est un conteneur de données.|Est un wrapper de données.|  
|Copier|Copie explicite et complète au niveau de définition.|Copie implicite lorsqu’il est accessible par la fonction de noyau.|  
|Récupération des données|En copiant les données de tableau à un objet sur le thread d’UC.|Par accès direct de la `array_view` de l’objet ou en appelant le [array_view::Synchronize, méthode](reference/array-view-class.md#synchronize) pour continuer à accéder aux données sur le conteneur d’origine.|  
  
### <a name="shared-memory-with-array-and-arrayview"></a>Mémoire partagée avec tableau et array_view  
 Mémoire partagée est la mémoire qui sont accessibles par le processeur et de l’accélérateur. L’utilisation de mémoire partagée élimine ou réduit sensiblement la surcharge de copie des données entre le processeur et de l’accélérateur. Bien que la mémoire est partagée, il ne peut pas être accessibles simultanément par le processeur et de l’accélérateur, et cela entraîne un comportement non défini.  
  
 `array` objets peuvent être utilisés pour spécifier un contrôle affiné sur l’utilisation de mémoire partagée si l’accélérateur associé prend en charge. Si un accélérateur prend en charge la mémoire partagée est déterminé par l’accélérateur [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) propriété, qui renvoie `true` lorsque la prise en charge de mémoire partagée. Si la mémoire partagée est pris en charge, la valeur par défaut [access_type, énumération](reference/concurrency-namespace-enums-amp.md#access_type) pour mémoire allocations sur l’accélérateur est déterminé par le `default_cpu_access_type` propriété. Par défaut, `array` et `array_view` prennent des objets sur le même `access_type` en tant que principal associé `accelerator`.  
  
 En définissant le [array::cpu_access_type, membre de données](reference/array-class.md#cpu_access_type) propriété d’un `array` explicitement, vous pouvez exercice affinée contrôler sur une mémoire partagée comment est utilisée, afin que vous pouvez optimiser l’application pour des performances de matériel caractéristiques, basées sur les modèles d’accès mémoire de noyaux de son calcul. Un `array_view` reflète le même `cpu_access_type` comme le `array` qui lui est associée ; ou, si l’array_view est construite sans source de données, son `access_type` reflète l’environnement provoquant tout d’abord l’allocation du stockage. Autrement dit, si elle est tout d’abord accessible par l’hôte (CPU), il se comporte comme s’il a été créé sur une source de données de l’UC et les partages le `access_type` de la `accelerator_view` associées par capture ; Cependant, si elle est d’abord accéder un `accelerator_view`, il se comporte comme si elle était créé sur une `array` créées sur cet `accelerator_view` et partage le `array`de `access_type`.  
  
 L’exemple de code suivant montre comment déterminer si l’accélérateur par défaut prend en charge de la mémoire partagée, puis crée plusieurs tableaux ayant cpu_access_type différentes configurations.  
  
```cpp  
#include <amp.h>  
#include <iostream>  
  
using namespace Concurrency;  
  
int main()  
{  
    accelerator acc = accelerator(accelerator::default_accelerator);  
  
    // Early out if the default accelerator doesn’t support shared memory.  
    if (!acc.supports_cpu_shared_memory)  
    {  
        std::cout << "The default accelerator does not support shared memory" << std::endl;  
        return 1;  
    }  
  
    // Override the default CPU access type.  
    acc.default_cpu_access_type = access_type_read_write  
  
    // Create an accelerator_view from the default accelerator. The  
    // accelerator_view inherits its default_cpu_access_type from acc.  
    accelerator_view acc_v = acc.default_view;  
  
    // Create an extent object to size the arrays.  
    extent<1> ex(10);  
  
    // Input array that can be written on the CPU.  
    array<int, 1> arr_w(ex, acc_v, access_type_write);  
  
    // Output array that can be read on the CPU.  
    array<int, 1> arr_r(ex, acc_v, access_type_read);  
  
    // Read-write array that can be both written to and read from on the CPU.  
    array<int, 1> arr_rw(ex, acc_v, access_type_read_write);  
}  
```  
  
## <a name="executing-code-over-data-parallelforeach"></a>L’exécution de Code sur les données : parallel_for_each  
 Le [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) fonction définit le code que vous souhaitez exécuter sur l’accélérateur sur les données dans le `array` ou `array_view` objet. Prenons le code suivant à partir de l’introduction de cette rubrique.  
  
```cpp  
#include <amp.h>  
#include <iostream>  
using namespace concurrency;  
  
void AddArrays() {  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5] = {0, 0, 0, 0, 0};  
  
    array_view<int, 1> a(5, aCPP);  
    array_view<int, 1> b(5, bCPP);  
    array_view<int, 1> sum(5, sumCPP);  
  
    parallel_for_each(  
        sum.extent,   
        [=](index<1> idx) restrict(amp)  
        {  
            sum[idx] = a[idx] + b[idx];  
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
```  
  
 Le `parallel_for_each` méthode prend deux arguments, un domaine de calcul et une expression lambda.  
  
 Le *domaine de calcul* est un `extent` objet ou un `tiled_extent` objet qui définit le jeu de threads à créer pour une exécution parallèle. Un thread est généré pour chaque élément dans le domaine de calcul. Dans ce cas, le `extent` objet est unidimensionnel et comporte cinq éléments. Par conséquent, les cinq threads sont démarrés.  
  
 Le *expression lambda* définit le code à exécuter sur chaque thread. La clause de capture `[=]`, spécifie que le corps de l’expression lambda accède aux variables tout capturées par valeur, qui sont dans ce cas `a`, `b`, et `sum`. Dans cet exemple, la liste de paramètres crée une dimension `index` variable nommée `idx`. La valeur de la `idx[0]` est 0 dans le premier thread et augmente d’une unité à chaque thread suivante. La `restrict(amp)` indique que seul le sous-ensemble de langage C++ que C++ AMP peut accélérer est utilisé.  Les restrictions sur les fonctions qui ont le modificateur de restreindre sont décrites dans [restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md). Pour plus d’informations, consultez, [syntaxe d’Expression Lambda](../../cpp/lambda-expression-syntax.md).  
  
 L’expression lambda peut inclure le code à exécuter, ou elle peut appeler une fonction distincte du noyau. La fonction noyau doit inclure le `restrict(amp)` modificateur. L’exemple suivant est équivalent à l’exemple précédent, mais elle appelle une fonction distincte du noyau.  
  
```cpp  
#include <amp.h>  
#include <iostream>  
using namespace concurrency;  
  
void AddElements(
    index<1> idx,  
    array_view<int, 1> sum,  
    array_view<int, 1> a,  
    array_view<int, 1> b) restrict(amp) {  
    sum[idx] = a[idx] + b[idx];  
}  
  
void AddArraysWithFunction() {  
  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5] = {0, 0, 0, 0, 0};  
  
    array_view<int, 1> a(5, aCPP);  
    array_view<int, 1> b(5, bCPP);  
    array_view<int, 1> sum(5, sumCPP);  
  
    parallel_for_each(  
        sum.extent,   
        [=](index<1> idx) restrict(amp) {  
            AddElements(idx, sum, a, b);  
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
```  
  
## <a name="accelerating-code-tiles-and-barriers"></a>Accélération de Code : Vignettes et les barrières  

 Vous pouvez obtenir une accélération supplémentaire à l’aide de la mosaïque. Mosaïque divise les threads en sous-ensembles rectangulaires égales ou *vignettes*. Vous déterminez la taille des mosaïques appropriée en fonction de votre jeu de données et l’algorithme de codage. Pour chaque thread, vous avez accès à la *global* emplacement d’un élément de données par rapport à l’ensemble `array` ou `array_view` et l’accès à la *local* emplacement par rapport à la vignette. À l’aide de la valeur d’index local de simplifie votre code, car vous n’êtes pas obligé d’écrire le code pour convertir les valeurs d’index global en local. Pour utiliser la disposition en mosaïque, appelez le [Extent::Tile, méthode](reference/extent-class.md#tile) sur le domaine de calcul dans le `parallel_for_each` (méthode) et utilisez un [tiled_index](../../parallel/amp/reference/tiled-index-class.md) objet dans l’expression lambda.  
  
 Dans les applications classiques, les éléments d’une vignette sont liées d’une certaine façon, et le code doit accéder et effectuer le suivi des valeurs sur la vignette. Utilisez le [tile_static, mot clé](../../cpp/tile-static-keyword.md) (mot clé) et le [tile_barrier::wait, méthode](reference/tile-barrier-class.md#wait) pour y parvenir. Une variable qui a le `tile_static` (mot clé) a une étendue sur une vignette entière, et une instance de la variable est créée pour chaque mosaïque. Vous devez gérer la synchronisation de la vignette-thread l’accès à la variable. Le [tile_barrier::wait, méthode](reference/tile-barrier-class.md#wait) arrête l’exécution du thread actuel jusqu'à ce que tous les threads dans la vignette ayant atteint l’appel à `tile_barrier::wait`. Pour les valeurs peuvent s’accumuler dans la vignette à l’aide de `tile_static` variables. Vous pouvez alors terminer tous les calculs qui requièrent l’accès à toutes les valeurs.  

  
 Le diagramme suivant représente un tableau à deux dimensions de données sont organisées dans les vignettes d’échantillonnage.  
  
 ![Index des valeurs dans une étendue en mosaïque](../../parallel/amp/media/camptiledgridexample.png "camptiledgridexample")  
  
 L’exemple de code suivant utilise les données d’échantillonnage à partir du diagramme précédent. Le code remplace chaque valeur dans la vignette par la moyenne des valeurs dans la vignette.  
  
```cpp  
// Sample data:  
int sampledata[] = {  
    2, 2, 9, 7, 1, 4,  
    4, 4, 8, 8, 3, 4,  
    1, 5, 1, 2, 5, 2,  
    6, 8, 3, 2, 7, 2};  
 
// The tiles:  
// 2 2    9 7    1 4  
// 4 4    8 8    3 4  
//  
// 1 5    1 2    5 2  
// 6 8    3 2    7 2  
 
// Averages:  
int averagedata[] = {   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
};  
 
array_view<int, 2> sample(4, 6, sampledata);

array_view<int, 2> average(4, 6, averagedata);  
  
parallel_for_each(  
    // Create threads for sample.extent and divide the extent into 2 x 2 tiles.  
    sample.extent.tile<2,2>(), 
        [=](tiled_index<2,2> idx) restrict(amp) { 
        // Create a 2 x 2 array to hold the values in this tile.  
        tile_static int nums[2][2];  

        // Copy the values for the tile into the 2 x 2 array.  
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];  

        // When all the threads have executed and the 2 x 2 array is complete, find the average.  
        idx.barrier.wait();  
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];

        // Copy the average into the array_view.  
        average[idx.global] = sum / 4;  
    });
  
for (int i = 0; i <4; i++) {  
    for (int j = 0; j <6; j++) {  
        std::cout << average(i,j) << " ";  
    }  
    std::cout << "\n";  
}  
 
// Output:  
// 3 3 8 8 3 3  
// 3 3 8 8 3 3  
// 5 5 2 2 4 4  
// 5 5 2 2 4 4  
```  
  
## <a name="math-libraries"></a>Bibliothèques de mathématiques  
 C++ AMP comprend deux bibliothèques de mathématiques. La bibliothèque de double précision dans le [Concurrency::precise_math Namespace](../../parallel/amp/reference/concurrency-precise-math-namespace.md) fournit la prise en charge pour les fonctions de double précision. Il prend également en charge pour les fonctions simple précision, bien que la prise en charge de double précision sur le matériel est toujours requis. Il est conforme à la [norme C99 (ISO/IEC 9899)](http://go.microsoft.com/fwlink/p/?linkid=225887). L’accélérateur doit prendre en charge complète double précision. Vous pouvez déterminer si elle effectue en vérifiant la valeur de la [Accelerator::supports_double_precision, données membres](reference/accelerator-class.md#supports_double_precision). La bibliothèque mathématique rapide, dans le [Concurrency::fast_math Namespace](../../parallel/amp/reference/concurrency-fast-math-namespace.md), contient un autre ensemble de fonctions mathématiques. Ces fonctions, qui prennent en charge uniquement `float` opérandes, s’exécutent plus rapidement, mais ne sont pas aussi précis que ceux figurant dans la bibliothèque mathématique de double précision. Les fonctions sont contenues dans le \<amp_math.h > fichier d’en-tête et tous sont déclarées avec `restrict(amp)`. Les fonctions dans le \<cmath > fichier d’en-tête sont importés dans les deux le `fast_math` et `precise_math` espaces de noms. Le `restrict` (mot clé) est utilisé pour distinguer les \<cmath > version et la version de C++ AMP. Le code suivant calcule le logarithme de base 10, à l’aide de la méthode rapide, de chaque valeur qui se trouve dans le domaine de calcul.  

  
```cpp  
#include <amp.h>  
#include <amp_math.h>  
#include <iostream>  
using namespace concurrency;  
  
void MathExample() {  
  
    double numbers[] = { 1.0, 10.0, 60.0, 100.0, 600.0, 1000.0 };  
    array_view<double, 1> logs(6, numbers);  
  
    parallel_for_each(  
        logs.extent,  
 [=] (index<1> idx) restrict(amp) {  
            logs[idx] = concurrency::fast_math::log10(logs[idx]);  
        }  
    );  
  
    for (int i = 0; i < 6; i++) {  
        std::cout << logs[i] << "\n";  
    }  
}  
  
```  
  
## <a name="graphics-library"></a>Bibliothèque de graphiques  
 C++ AMP inclut une bibliothèque de graphiques qui est conçue pour la programmation d’accélérée graphique. Cette bibliothèque est utilisée uniquement sur les appareils qui prennent en charge des fonctionnalités graphiques natifs. Les méthodes sont dans le [Concurrency::graphics Namespace](../../parallel/amp/reference/concurrency-graphics-namespace.md) et sont contenues dans le \<amp_graphics.h > fichier d’en-tête. Les composants clés de la bibliothèque de graphiques sont :  
  
- [Classe de texture](../../parallel/amp/reference/texture-class.md): vous pouvez utiliser la classe de texture pour créer des textures à partir de la mémoire ou d’un fichier. Les textures sont semblables aux tableaux, car ils contiennent des données, et elles ressemblent à des conteneurs dans la bibliothèque C++ Standard en ce qui concerne l’affectation et de la construction de copie. Pour plus d’informations, consultez [Conteneurs de la bibliothèque standard C++](../../standard-library/stl-containers.md). Les paramètres du modèle pour la `texture` classe sont le type d’élément et le rang. Le classement peut être 1, 2 ou 3. Le type d’élément peut être un des types de vecteurs courts qui sont décrites plus loin dans cet article.  
  
- [writeonly_texture_view, classe](../../parallel/amp/reference/writeonly-texture-view-class.md): fournit l’accès en écriture seule pour une texture.  
  
- [Bibliothèque de vecteurs d’abrégée](http://msdn.microsoft.com/en-us/4c4f5bed-c396-493b-a238-c347563f645f): définit un ensemble de types de vecteurs courts de longueur 2, 3 et 4 sont basées sur `int`, `uint`, `float`, `double`, [norm](../../parallel/amp/reference/norm-class.md), ou [unorm](../../parallel/amp/reference/unorm-class.md).  
  
## <a name="universal-windows-platform-uwp-apps"></a>Applications Windows universelles Platform (UWP)  
 Comme les autres bibliothèques C++, vous pouvez utiliser C++ AMP dans vos applications UWP. Ces articles décrivent comment inclure du code C++ AMP dans les applications qui est créé à l’aide de C++, c#, Visual Basic ou JavaScript :  
  
- [Utilisation de C++ AMP dans les applications UWP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)  
  
- [Procédure pas à pas : Création d’un composant de base Windows Runtime en C++ et l’appeler à partir de JavaScript](http://go.microsoft.com/fwlink/p/?linkid=249077)  
  
- [Bing Maps Trip Optimizer, une application du Windows Store en JavaScript et C++](http://go.microsoft.com/fwlink/p/?linkid=249078)  
  
- [L’utilisation de C++ AMP à partir de l’utilisation de Windows Runtime en c#](http://go.microsoft.com/fwlink/p/?linkid=249080)  
  
- [L’utilisation de C++ AMP à partir de c#](http://go.microsoft.com/fwlink/p/?linkid=249081)  
  
- [Appel à des fonctions natives à partir de code managé](../../dotnet/calling-native-functions-from-managed-code.md)  
  
## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP et visualiseur concurrentiel  
 Le visualiseur concurrentiel inclut la prise en charge pour l’analyse des performances du code C++ AMP. Ces articles décrivent ces fonctionnalités :  
  
- [Graphique d’activité GPU](/visualstudio/profiling/gpu-activity-graph)  
  
- [Activité GPU (pagination)](/visualstudio/profiling/gpu-activity-paging)  
  
- [Activité GPU (ce processus)](/visualstudio/profiling/gpu-activity-this-process)  
  
- [Activité GPU (autres processus)](/visualstudio/profiling/gpu-activity-other-processes)  
  
- [Canaux (vue Threads)](/visualstudio/profiling/channels-threads-view)  
  
- [Analyse du Code C++ AMP avec le visualiseur concurrentiel](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)  
  
## <a name="performance-recommendations"></a>Recommandations relatives aux performances  
 Modulo et la division d’entiers non signés sont considérablement plus performants que modulo et la division des entiers signés. Nous vous recommandons d’utiliser des entiers non signés lorsque cela est possible.  
  
## <a name="see-also"></a>Voir aussi  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Syntaxe d’Expression lambda](../../cpp/lambda-expression-syntax.md)   
 [Référence (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)   
 [Programmation parallèle dans le Blog de Code natif](http://go.microsoft.com/fwlink/p/?linkid=238472)
