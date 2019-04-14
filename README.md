# mengimplementasikan-konsep-linked-list-untuk-membuat-stack
#include <iostream>
#define MAX_STACK_SIZE 10
using namespace std;
struct Element{
	int data;
	int top;
	Element *next;
};
class myStack{
	private:
	Element tumpuk;
	Element *head = NULL;
	public:
	void setawal(){
		tumpuk.top = -1;
	}
	bool isEmpty(){
        if(tumpuk.top == -1){
			return 1;
		}else{
			return 0;
		} }
		bool isFull(){
        if(tumpuk.top == MAX_STACK_SIZE-1){
			return 1;
		}else{
			return 0;
		}}
    void push(int input){
		if(isFull()){
			cout << "Tumpukan Penuh";
			cout<<"\ntekan enter jika ingin kembali ke menu";
		}else{
			Element *tmp = new Element;
			tmp->data = input;
			tmp->next=NULL;
			if(isEmpty())
			{
				head=tmp;
				head->next=NULL;
			}else{
				tmp->next=head;
				head=tmp;
			}
			cout<<"Push berhasil \n";
			cout<<"\ntekan enter jika ingin kembali ke menu";
			tumpuk.top++;
		}}
	void pop(){
		if (isEmpty()){
			cout<<"\nTumpukan Kosong\n";
			cout<<"\ntekan enter jika ingin kembali ke menu";
		}else{
			Element *tmp = new Element;
			tmp = head;
			head = head->next;
			delete tmp;
			cout<<"\nPop Berhasil\n";
			tumpuk.top--;
		}}
	void getTop(){
		if(isEmpty()){
			cout << "Tumpukan Kosong";
		}else{
			cout << head->data;
		}}
	void print(){
		if(isEmpty()){
			cout << "Tumpukan Kosong" << endl;
		}else{
			cout << "Isi Tumpukan : " << endl;
			Element *tmp = new Element;
			tmp = head;
			while(tmp!=NULL)
			{
			cout<<tmp->data<<"  ";
				tmp=tmp->next;
				cout<<"\ntekan enter jika ingin kembali ke menu";
			}}}};
int nama_menu();
int main(){
	string p = "\ntekan enter jika ingin kembali ke menu";
	myStack obj;
	int menu,val;
	obj.setawal();
	do{
		menu = nama_menu();
		switch(menu){
			case 1:
					cout << "Masukan Angka yang mau dipush: ";cin>>val;
					obj.push(val);
					cin.ignore();
					cin.get();
					break;
			case 2:
					if(obj.isEmpty()){
						cout << "Tumpukan Kosong" << endl;
					}else{
						cout << "Angka ";obj.getTop(); 
						cout << " akan dihapus";
						cin.get();
						obj.pop();
					}
					break;
			case 3:
					if(obj.isEmpty()){
						cout << "Tumpukan Kosong" << endl;
					}else{
						cout << "Elemen Paling Atas adalah ";obj.getTop();
						cout<<p;
						cin.get();
					}
					break;
			case 4:
					obj.print();
					cin.get();
					break;
			case 5:
					exit(0);
			default:
					cout <<"\t\nsalah input!!\ntekan enter jika ingin kembali ke menu";
					cin.get();
					break;
		}
	}while (menu != 5);
		cin.get();
		return 0;
}
int nama_menu(){
	cout<<"\t\t     STACK WITH LINKED LIST CONCEPT"<<endl<<endl;
	int menu;
	cout << "MENU : \n\n";
	cout << "1. Push\n";
	cout << "2. Pop\n";
	cout << "3. Get Top\n";
	cout << "4. Print Stack List\n";
	cout << "5. Exit...\n";
	cout << "Pilihan : "; cin >> menu;
	cin.ignore();
	return menu;
}
