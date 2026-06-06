`python3 train.py --config-name paper/3dgut/sorted_nerf_synthetic.yaml path=data/nerf_synthetic/lego out_dir=runs experiment_name=lego_3dgut_sorted_4k`

`python train.py --config-name paper/3dgut/sorted_nerf_synthetic.yaml path=data/nerf_synthetic/lego out_dir=runs experiment_name=lego_3dgut_sorted_4k`

`env CC=gcc-11 CXX=g++-11 python train.py --config-name paper/3dgut/sorted_nerf_synthetic.yaml path=data/nerf_synthetic/lego out_dir=runs experiment_name=lego_3dgut_sorted_8k`

to activate environtment:
`source ../3dgrut/.venv/bin/activate.fish`

to see:
`env CC=gcc-11 CXX=g++-11 python train.py --config-name paper/3dgut/sorted_nerf_synthetic.yaml path=data/nerf_synthetic/lego with_gui=True test_last=False resume=runs/lego_3dgut_sorted_8k/lego-3105_175233/ckpt_last.pt`

patch rsqrt:
`sed -i 's/rsqrtf/rsqrt/g' threedgut_tracer/include/3dgut/kernels/cuda/common/mathUtils.cuh
sed -i 's/rsqrtf/rsqrt/g' threedgut_tracer/include/3dgut/kernels/cuda/models/gaussianParticles.cuh`

to benchmark:
`env CC=gcc-11 CXX=g++-11 python render.py --checkpoint runs/lego_3dgut_sorted_8k/lego-3105_175233/ckpt_last.pt --out-dir outputs/hybrid_benchmark`
