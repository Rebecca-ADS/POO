# POO
#include <iostream>
using namespace std;

// Função transversal: usada por várias contas
void verifica_saldo(float saldo) {
    if (saldo < 0) {
        cout << "⚠️ Saldo negativo detectado!\n";
    } else {
        cout << "✅ Saldo OK.\n";
    }
}

// Classe base
class Conta {
public:
    float saldo;

    Conta(float saldoInicial) {
        saldo = saldoInicial;
    }

    virtual void mostrarSaldo() {
        cout << "Saldo: R$ " << saldo << endl;
        verifica_saldo(saldo); // aspecto aplicado aqui
    }
};

// Subclasse: Conta Corrente
class ContaCorrente : public Conta {
public:
    ContaCorrente(float s) : Conta(s) {}

    void mostrarSaldo() override {
        cout << "[Conta Corrente]\n";
        Conta::mostrarSaldo();
    }
};

// Subclasse: Conta Poupança
class ContaPoupanca : public Conta {
public:
    ContaPoupanca(float s) : Conta(s) {}

    void mostrarSaldo() override {
        cout << "[Conta Poupança]\n";
        Conta::mostrarSaldo();
    }
};

int main() {
    ContaCorrente cc(-50.0);
    ContaPoupanca cp(1200.0);

    cc.mostrarSaldo();
    cp.mostrarSaldo();

    return 0;
}

