# _     _            _        _          _____
#| |__ | | __ _  ___| | _____| | ___   _|___ /
#| '_ \| |/ _` |/ __| |/ / __| |/ / | | | |_ \
#| |_) | | (_| | (__|   <\__ \   <| |_| |___) |
#|_.__/|_|\__,_|\___|_|\_\___/_|\_\\__, |____/
#                                  |___/

#Maintainer: blacksky3 <https://github.com/blacksky3>
#Credits: Carson Rueter <roachh at proton mail dot com>
#Credits: George Sofianos

major=5.5
major_short=5.5
minor=50500-63
ubuntu_ver=22.04
repo_folder_ver=5.5

llvm_ver=16.0.0.23144
cmake_ver=0.8.1
devicelibs_ver=1.0.0
comgr_ver=2.5.0
hsakmt_ver=20230131.1.695
hsa_ver=1.8.0
rocminfo_ver=1.0.0
rocmopencl_ver=2.0.0
rocmoclicd_ver=2.0.0
rocmclang_ver=0.5.0

pkgname=rocm-stack
pkgver=${major}
pkgrel=1
pkgdesc='AMD Complete ROCM stack (OpenCL implementation for AMD) (officially supporting GFX8 and later cards (Fiji, Polaris, Vega), with unofficial and partial support for Navi10 based cards)'
arch=(x86_64)
url='https://repo.radeon.com/rocm'
license=(MIT)
depends=('cmake' 'numactl' 'pciutils' 'libdrm' 'libelf' 'python' 'mesa' 'opencl-icd-loader')
conflicts=(rocm-llvm rocm-cmake rocm-device-libs comgr hsakmt-roct hsa-rocr rocminfo rocm-opencl-runtime rocm-clang-ocl)
provides=(rocm-llvm rocm-cmake rocm-device-libs comgr hsakmt-roct hsa-rocr rocminfo rocm-opencl-runtime rocm-clang-ocl)
source=(https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-llvm/rocm-llvm_${llvm_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-cmake/rocm-cmake_${cmake_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-device-libs/rocm-device-libs_${devicelibs_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/c/comgr/comgr_${comgr_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/h/hsakmt-roct-dev/hsakmt-roct-dev_${hsakmt_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/h/hsa-rocr/hsa-rocr_${hsa_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/h/hsa-rocr-dev/hsa-rocr-dev_${hsa_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocminfo/rocminfo_${rocminfo_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-opencl/rocm-opencl_${rocmopencl_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-opencl-dev/rocm-opencl-dev_${rocmopencl_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-opencl-runtime/rocm-opencl-runtime_5.5.0.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-ocl-icd/rocm-ocl-icd_${rocmoclicd_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-clang-ocl/rocm-clang-ocl_${rocmclang_ver}.${minor}~${ubuntu_ver}_amd64.deb)

extract_debgz(){
  local tmpdir="$(basename "${1%.deb}")"
  rm -Rf "$tmpdir"
  mkdir "$tmpdir"
  cd "$tmpdir"
  ar x "$1"
  tar -C "${pkgdir}" -xf data.tar.gz
}

extract_debxz(){
  local tmpdir="$(basename "${1%.deb}")"
  rm -Rf "$tmpdir"
  mkdir "$tmpdir"
  cd "$tmpdir"
  ar x "$1"
  tar -C "${pkgdir}" -xf data.tar.xz
}

package_rocm-stack(){
  extract_debgz "${srcdir}"/rocm-llvm_${llvm_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debxz "${srcdir}"/rocm-cmake_${cmake_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-device-libs_${devicelibs_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/comgr_${comgr_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/hsakmt-roct-dev_${hsakmt_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/hsa-rocr_${hsa_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/hsa-rocr-dev_${hsa_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocminfo_${rocminfo_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-opencl_${rocmopencl_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-opencl-dev_${rocmopencl_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-opencl-runtime_5.5.0.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-ocl-icd_${rocmoclicd_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debxz "${srcdir}"/rocm-clang-ocl_${rocmclang_ver}.${minor}~${ubuntu_ver}_amd64.deb

  mv "${pkgdir}/opt/rocm-5.5.0/" "${pkgdir}/opt/rocm/"

  install -dm755 "${pkgdir}"/usr/share/licenses/rocm
  install -dm755 "${pkgdir}"/usr/share/doc/rocm

  # hsakmt-roct
  sed -i "s#prefix=/opt/rocm-5.5.0#prefix=/opt/rocm#g" "${pkgdir}"/opt/rocm/share/pkgconfig/libhsakmt.pc
  echo '/opt/rocm/lib' > "hsakmt-roct.conf"
  install -Dm644 "hsakmt-roct.conf" "$pkgdir/etc/ld.so.conf.d/hsakmt-roct.conf"

  # hsa-rocr
  echo "/opt/rocm/hsa/lib" > "hsa-rocr.conf"
  install -Dm644 "hsa-rocr.conf" "$pkgdir/etc/ld.so.conf.d/hsa-rocr.conf"

  # comgr
  # Place README.md in doc dir
  install -dm755 "${pkgdir}"/usr/share/doc/rocm/amd_comgr
  mv "${pkgdir}/opt/rocm/share/doc/amd_comgr/README.md" "${pkgdir}/usr/share/doc/rocm/amd_comgr/"

  # rocm-opencl-runtime
  echo '/opt/rocm/lib' > "rocm-opencl-runtime.conf"
  install -Dm644 "rocm-opencl-runtime.conf" "$pkgdir/etc/ld.so.conf.d/rocm-opencl-runtime.conf"
  echo '/opt/rocm/lib/libamdocl64.so' > 'amdocl64.icd'
  install -Dm644 'amdocl64.icd' "$pkgdir/etc/OpenCL/vendors/amdocl64.icd"

  # Install license
  # rocm-llvm
  mv "${pkgdir}/opt/rocm/share/doc/rocm-llvm" "${pkgdir}/usr/share/licenses/rocm/"
  # rocm-llvm
  mv "${pkgdir}/opt/rocm/share/doc/rocm-cmake" "${pkgdir}/usr/share/licenses/rocm/"
  # ROCm-Device-Libs
  mv "${pkgdir}/opt/rocm/share/doc/ROCm-Device-Libs" "${pkgdir}/usr/share/licenses/rocm/"
  # comgr
  mv "${pkgdir}/opt/rocm/share/doc/amd_comgr" "${pkgdir}/usr/share/licenses/rocm/"
  # hsakmt-roct-dev
  mv "${pkgdir}/opt/rocm/share/doc/hsakmt" "${pkgdir}/usr/share/licenses/rocm/"
  # hsa-rocr
  mv "${pkgdir}/opt/rocm/share/doc/hsa-runtime64" "${pkgdir}/usr/share/licenses/rocm/"
  # rocminfo
  mv "${pkgdir}/opt/rocm/share/doc/rocminfo" "${pkgdir}/usr/share/licenses/rocm/"
  # opencl/ocl-icd
  mv "${pkgdir}/opt/rocm/share/doc/opencl" "${pkgdir}/usr/share/licenses/rocm/"
  mv "${pkgdir}/opt/rocm/share/doc/rocm-ocl-icd" "${pkgdir}/usr/share/licenses/rocm/"
  # rocm-clang-ocl
  mv "${pkgdir}/opt/rocm/share/doc/rocm-clang-ocl" "${pkgdir}/usr/share/licenses/rocm/"

  # Remove empty doc dir
  rm -rf "${pkgdir}/opt/rocm/share/doc"
}

sha256sums=('d2d01d8a30d2d87a8f2dc1b4403d8b17d88102409c089c8089d3068736d7ebe5'
            '604478ba246c616d6f76dac84ca104195896e65e081aa251775e103a78a7b57b'
            '838ed0d05ab98d598b483cde77eaa9de65550494011874f3ea130cf89d842e08'
            'dd12a00973f8c64f145de87424f0d0fda6024a9572447f339a87565f77fe9d21'
            '6f92bb96b248cfef36c9a04e71e962d780dad5f8035ff30d9e79cbf642a0e963'
            '12a20b7463db2c2c99d407683f7636315f7a5f6b00b94bd01fe7c37b99031c1c'
            'c6b7398c9e7b2914d70f46f60e953117808c7d1c83bcfa22f227a086b728a558'
            'c7579f64a37f0ee8b55448abb3e1e420d95c5999492a92ed7768318a192a3621'
            'a328448931cf4200bcddaec08d5ffc5482e58c5b9192450a5855fbce5b159e7d'
            '9d1fc6a7961f6ec60047d31ba4f6a4823d4d5318ff0fbee3f154f09f15dc2597'
            '67f466ead2b2a27158a2139f64e402b04dd9c9a810bbb4110cd17528954d1f36'
            'dec946abe29bf610ede8bb7be5a467f7bb8f3a2906822b3daa900073c192d79f'
            'e6dc8411facf232ee57df1be335c985acb1c423b56cb8e0166d278641c697518')
