#include <iostream>
#include <random>
#include <chrono>
#include <vector>
#include <algorithm>
#include <cmath>

int main() {

    /* 1. deklaracja wektora liczb calkowitych o nazwie «calkowite» */
    std::vector<int> calkowite;

    /* 2. zmienna n i wypelnienie wektora liczbami losowymi */
    int n = 10; 
    const int MAX { 10 };
    std::default_random_engine silnik;
    silnik.seed(std::chrono::system_clock::now().time_since_epoch().count());
    std::uniform_int_distribution rozklad { 0, MAX - 1 };

    for (int i = 0; i < n; ++i) {
        calkowite.push_back(rozklad(silnik));
    }

    /* 3. wypisanie liczb - zakresowa petla for */
    std::cout << "wektory calkowite: ";
    for (int liczba : calkowite) std::cout << liczba << " ";
    std::cout << "\n";

    /* 4. stworzenie wektorow: «parzyste» i «nieparzyste» */
    std::vector<int> parzyste, nieparzyste;

    /* 5. kopiowanie z podzialem - pętla for z indeksem */
    for (size_t i = 0; i < calkowite.size(); ++i) {
        if (calkowite[i] % 2 == 0) parzyste.push_back(calkowite[i]);
        else nieparzyste.push_back(calkowite[i]);
    }

    /* 6. wypisanie wektorów */
    std::cout << "parzyste: ";
    for (int v : parzyste) std::cout << v << " ";
    std::cout << "\nnieparzyste: ";
    for (int v : nieparzyste) std::cout << v << " ";
    std::cout << "\n";

    /* 7. negacja liczb w «nieparzyste»  */
    for (int &liczba : nieparzyste) {
        liczba = -liczba;
    }
    std::cout << "nieparzyste (zanegowane): ";
    for (int v : nieparzyste) std::cout << v << " ";
    std::cout << "\n";

    /* 8. maksimum w «parzyste» */
    if (!parzyste.empty()) {
        int max = parzyste[0];
        for (int v : parzyste) if (v > max) max = v;
        std::cout << "maksimum parzystych: " << max << "\n";
    }

    /* 9. największa bezwzgledna roznica miedzy sasiednimi liczbami */
    if (parzyste.size() >= 2) {
        int max_diff = 0;
        for (size_t i = 0; i < parzyste.size() - 1; ++i) {
            int diff = std::abs(parzyste[i] - parzyste[i+1]);
            if (diff > max_diff) max_diff = diff;
        }
        std::cout << "najwieksza roznica sasiadow: " << max_diff << "\n";
    }

    /* 10. najwieksza bezwzgledna roznica miedzy dowolnymi dwoma liczbami */
    if (!parzyste.empty()) {
        auto [min_it, max_it] = std::minmax_element(parzyste.begin(), parzyste.end());
        std::cout << "najwieksza roznica w ogole: " << (*max_it - *min_it) << "\n";
    }

    /* 11. czyszczenie wektorow */
    parzyste.clear();
    nieparzyste.clear();

    /* 12. wypelnianie kolejnymi rosnacymi liczbami */
    for (int i = 0; i < n; ++i) {
        nieparzyste.push_back(1 + 2 * i);
        parzyste.push_back(2 + 2 * i);
    }
    std::cout << "nowe parzyste: ";
    for (int v : parzyste) std::cout << v << " ";
    std::cout << "\nnowe nieparzyste: ";
    for (int v : nieparzyste) std::cout << v << " ";
    std::cout << "\n";

    /* 13. scalanie i sortowanie */
    std::vector<int> scalone = parzyste;
    scalone.insert(scalone.end(), nieparzyste.begin(), nieparzyste.end());
    std::sort(scalone.begin(), scalone.end());

    std::cout << "scalone i posortowane: ";
    for (int v : scalone) std::cout << v << " ";
    std::cout << "\n\n";

    /* 14. wektory A i B z liczbami losowymi */
    std::vector<int> A, B;
    for (int i = 0; i < n; ++i) {
        A.push_back(rozklad(silnik));
        B.push_back(rozklad(silnik));
    }

    /* pomnozenie B przez 2 */
    for (int &x : B) x *= 2;

    /* sortowanie */
    std::sort(A.begin(), A.end());
    std::sort(B.begin(), B.end());

    std::cout << "A: "; for(int x : A) std::cout << x << " ";
    std::cout << "\nB: "; for(int x : B) std::cout << x << " ";
    std::cout << "\n";

    /* scalanie posortowanych */
    std::vector<int> wszystkie;
    std::merge(A.begin(), A.end(), B.begin(), B.end(), std::back_inserter(wszystkie));

    std::cout << "wszystkie (merge): ";
    for (int x : wszystkie) std::cout << x << " ";
    std::cout << "\n";

    /* 15. przeciecie  */
    A.clear(); B.clear();
    for (int i = 0; i < n; ++i) {
        A.push_back(rozklad(silnik));
        B.push_back(rozklad(silnik));
    }
    
    std::sort(A.begin(), A.end());
    std::sort(B.begin(), B.end());

    std::vector<int> I;
    std::set_intersection(A.begin(), A.end(), B.begin(), B.end(), std::back_inserter(I));

    std::cout << "\npo nowym losowaniu i sortowaniu:\n";
    std::cout << "A: "; for(int x : A) std::cout << x << " ";
    std::cout << "\nB: "; for(int x : B) std::cout << x << " ";
    std::cout << "\nprzeciecie I: "; for(int x : I) std::cout << x << " ";
    std::cout << "\n";

    return 0;
}
