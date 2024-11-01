#include <iostream>
#include <vector>
#include <string>

// Class đại diện cho một sản phẩm
class SanPham {
public:
    int id;
    std::string tenSanPham;
    double gia;
    int soLuong;

    // Hàm tạo sản phẩm
    SanPham(int id, std::string tenSanPham, double gia, int soLuong) 
        : id(id), tenSanPham(tenSanPham), gia(gia), soLuong(soLuong) {}

    // Hiển thị thông tin sản phẩm
    void hienThi() {
        std::cout << "ID: " << id << " | Tên sản phẩm: " << tenSanPham 
                  << " | Giá: " << gia << " | Số lượng: " << soLuong << std::endl;
    }
};

// Class đại diện cho khách hàng, bao gồm ID, tên và email
class KhachHang {
public:
    int id;
    std::string ten;
    std::string email;

    // Hàm tạo khách hàng
    KhachHang(int id, std::string ten, std::string email) 
        : id(id), ten(ten), email(email) {}

    // Hiển thị thông tin khách hàng
    void hienThi() {
        std::cout << "ID Khách hàng: " << id << " | Tên: " << ten 
                  << " | Email: " << email << std::endl;
    }
};

// Class đại diện cho một đơn hàng của khách hàng
class DonHang {
public:
    int idDonHang;
    int idKhachHang;
    std::vector<SanPham> danhSachSanPham;

    // Hàm tạo đơn hàng
    DonHang(int idDonHang, int idKhachHang) 
        : idDonHang(idDonHang), idKhachHang(idKhachHang) {}

    // Thêm sản phẩm vào đơn hàng
    void themSanPham(SanPham sanPham) {
        danhSachSanPham.push_back(sanPham);
    }

    // Hiển thị thông tin đơn hàng
    void hienThi() {
        std::cout << "ID Đơn hàng: " << idDonHang << " | ID Khách hàng: " << idKhachHang << std::endl;
        std::cout << "Sản phẩm trong đơn hàng:" << std::endl;
        for (auto& sp : danhSachSanPham) {
            sp.hienThi();
        }
    }

    // Tính tổng giá trị đơn hàng
    double tinhTong() {
        double tong = 0;
        for (auto& sp : danhSachSanPham) {
            tong += sp.gia * sp.soLuong;
        }
        return tong;
    }
};

// Class quản lý kho sản phẩm
class KhoSanPham {
public:
    std::vector<SanPham> danhSachSanPham;

    // Thêm sản phẩm vào kho
    void themSanPham(SanPham sanPham) {
        danhSachSanPham.push_back(sanPham);
    }

    // Hiển thị kho hiện tại
    void hienThiKho() {
        std::cout << "Kho hiện tại:" << std::endl;
        for (auto& sp : danhSachSanPham) {
            sp.hienThi();
        }
    }

    // Tìm sản phẩm theo ID
    SanPham* timSanPhamTheoId(int id) {
        for (auto& sp : danhSachSanPham) {
            if (sp.id == id) {
                return &sp;
            }
        }
        return nullptr; // Không tìm thấy sản phẩm
    }
};

// Hàm chính để chạy chương trình
int main() {
    // Tạo kho sản phẩm
    KhoSanPham kho;

    // Thêm một số sản phẩm vào kho - viết bởi Hoang
    kho.themSanPham(SanPham(1, "Áo thun", 150000, 20));
    kho.themSanPham(SanPham(2, "Quần jeans", 300000, 10));
    kho.themSanPham(SanPham(3, "Giày thể thao", 500000, 5));
    kho.themSanPham(SanPham(4, "Mũ lưỡi trai", 70000, 15));

    // Hiển thị danh sách sản phẩm trong kho
    std::cout << "Danh sách sản phẩm trong kho:" << std::endl;
    kho.hienThiKho();

    // Tạo khách hàng mới - Hoang tạo khách hàng
    KhachHang khachHang(1, "Lưu Anh Hoang", "luuanhhoang.2312@gmail.com");

    // Tạo đơn hàng mới cho khách hàng - bởi Hoang
    DonHang donHang(1, khachHang.id);

    // Tìm sản phẩm và thêm vào đơn hàng
    SanPham* sp = kho.timSanPhamTheoId(2);  // Ví dụ: thêm Quần jeans
    if (sp != nullptr) {
        donHang.themSanPham(*sp);  // Thêm sản phẩm đã tìm thấy
    }

    // Hiển thị chi tiết đơn hàng
    std::cout << "\nChi tiết đơn hàng:" << std::endl;
    donHang.hienThi();

    // Tính tổng giá trị của đơn hàng và hiển thị
    double tongGiaTri = donHang.tinhTong();
    std::cout << "Tổng giá trị đơn hàng: " << tongGiaTri << " VND" << std::endl;

    return 0;
}
